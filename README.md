-- 1. Database Design
-- Tables & Relationships
-- Patients – Manage patient details

CREATE TABLE Patients (
    patient_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    dob DATE,
    gender ENUM('M','F','Other'),
    phone VARCHAR(15),
    address VARCHAR(255),
    registered_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);


INSERT INTO Patients (name, dob, gender, phone, address)
VALUES
('Rajesh Kumar', '1985-04-12', 'M', '9876543210', 'Patna, Bihar'),
('Sonia Singh', '1990-11-23', 'F', '9123456780', 'Gaya, Bihar'),
('Ankit Sharma', '1992-06-15', 'M', '9012345678', 'Bihar Sharif, Bihar'),
('Priya Kumari', '1995-08-20', 'F', '9988776655', 'Munger, Bihar'),
('Vikas Yadav', '1988-03-05', 'M', '9765432109', 'Muzaffarpur, Bihar'),
('Ritu Verma', '1991-09-12', 'F', '9654321098', 'Darbhanga, Bihar'),
('Amit Singh', '1987-12-01', 'M', '9543210987', 'Chapra, Bihar'),
('Neha Gupta', '1994-01-19', 'F', '9432109876', 'Hajipur, Bihar'),
('Suresh Kumar', '1989-07-25', 'M', '9321098765', 'Sitamarhi, Bihar'),
('Pooja Sharma', '1993-05-10', 'F', '9210987654', 'Samastipur, Bihar'),
-- Add 40 more like this
('Patient11','1986-02-14','M','9000000011','Address11'),
('Patient12','1990-03-21','F','9000000012','Address12'),
('Patient13','1992-07-30','M','9000000013','Address13'),
('Patient14','1995-01-05','F','9000000014','Address14'),
('Patient15','1988-08-19','M','9000000015','Address15'),
('Patient16','1991-11-22','F','9000000016','Address16'),
('Patient17','1989-12-31','M','9000000017','Address17'),
('Patient18','1993-03-18','F','9000000018','Address18'),
('Patient19','1992-06-25','M','9000000019','Address19'),
('Patient20','1994-09-09','F','9000000020','Address20'),
('Patient21','1985-05-13','M','9000000021','Address21'),
('Patient22','1987-10-14','F','9000000022','Address22'),
('Patient23','1990-12-25','M','9000000023','Address23'),
('Patient24','1992-02-28','F','9000000024','Address24'),
('Patient25','1991-07-07','M','9000000025','Address25'),
('Patient26','1993-08-16','F','9000000026','Address26'),
('Patient27','1986-09-19','M','9000000027','Address27'),
('Patient28','1988-11-23','F','9000000028','Address28'),
('Patient29','1990-01-30','M','9000000029','Address29'),
('Patient30','1992-03-11','F','9000000030','Address30'),
('Patient31','1991-04-22','M','9000000031','Address31'),
('Patient32','1993-05-13','F','9000000032','Address32'),
('Patient33','1985-06-25','M','9000000033','Address33'),
('Patient34','1987-07-15','F','9000000034','Address34'),
('Patient35','1989-08-05','M','9000000035','Address35'),
('Patient36','1990-09-14','F','9000000036','Address36'),
('Patient37','1992-10-19','M','9000000037','Address37'),
('Patient38','1994-11-23','F','9000000038','Address38'),
('Patient39','1986-12-30','M','9000000039','Address39'),
('Patient40','1988-01-10','F','9000000040','Address40'),
('Patient41','1990-02-20','M','9000000041','Address41'),
('Patient42','1992-03-30','F','9000000042','Address42'),
('Patient43','1994-04-12','M','9000000043','Address43'),
('Patient44','1991-05-25','F','9000000044','Address44'),
('Patient45','1987-06-16','M','9000000045','Address45'),
('Patient46','1989-07-30','F','9000000046','Address46'),
('Patient47','1990-08-19','M','9000000047','Address47'),
('Patient48','1992-09-09','F','9000000048','Address48'),
('Patient49','1994-10-21','M','9000000049','Address49'),
('Patient50','1991-11-11','F','9000000050','Address50');
 
 SELECT * FROM Patients;
 
-- Doctors – Hospital doctors


CREATE TABLE Doctors (
    doctor_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    specialty VARCHAR(50),
    phone VARCHAR(15),
    email VARCHAR(100),
    hire_date DATE
);

INSERT INTO Doctors (name, specialty, phone, email, hire_date)
VALUES
('Dr. Ramesh Kumar', 'Cardiology', '9800000011', 'ramesh@hospital.com', '2015-03-10'),
('Dr. Anjali Sharma', 'Neurology', '9800000012', 'anjali@hospital.com', '2016-07-15'),
('Dr. Saurabh Singh', 'Orthopedics', '9800000013', 'saurabh@hospital.com', '2017-05-20'),
('Dr. Pooja Verma', 'Gynecology', '9800000014', 'pooja@hospital.com', '2018-01-10'),
('Dr. Amit Yadav', 'Pediatrics', '9800000015', 'amit@hospital.com', '2014-12-05'),
-- Add 10 more
('Dr. Neha Gupta','Dermatology','9800000016','neha@hospital.com','2015-08-12'),
('Dr. Vikram Singh','ENT','9800000017','vikram@hospital.com','2016-09-11'),
('Dr. Sunita Rao','Gastroenterology','9800000018','sunita@hospital.com','2017-10-21'),
('Dr. Rajeev Kumar','Oncology','9800000019','rajeev@hospital.com','2018-11-17'),
('Dr. Seema Sharma','Cardiology','9800000020','seema@hospital.com','2019-03-12');

 SELECT * FROM Doctors;

 
-- Appointments – Patient appointments with doctors


CREATE TABLE Appointments (
    appointment_id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT,
    doctor_id INT,
    appointment_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status ENUM('Scheduled','Completed','Cancelled') DEFAULT 'Scheduled',
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id),
    FOREIGN KEY (doctor_id) REFERENCES Doctors(doctor_id)
);

INSERT INTO Appointments (patient_id, doctor_id, appointment_date, status)
VALUES
(1,1,'2025-09-01 10:00:00','Completed'),
(2,2,'2025-09-01 11:00:00','Completed'),
(3,3,'2025-09-01 12:00:00','Scheduled'),
(4,1,'2025-09-02 10:30:00','Scheduled'),
(5,2,'2025-09-02 11:30:00','Cancelled'),
-- add 45 more with random patient_id & doctor_id
(6,3,'2025-09-02 12:30:00','Completed'),
(50,5,'2025-09-10 15:00:00','Scheduled');

SELECT * FROM Appointments ;

-- 4.Treatments – Medical procedures or treatments

CREATE TABLE Treatments (
    treatment_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    cost DECIMAL(10,2)
);

INSERT INTO Treatments (name, cost)
VALUES
('MRI Scan', 5000.00),
('X-Ray', 800.00),
('Blood Test', 500.00),
('Physiotherapy', 1500.00),
('Surgery', 25000.00),
('Ultrasound', 1200.00),
('ECG', 600.00),
('Vaccination', 300.00),
('Dental Cleaning', 700.00),
('Eye Checkup', 400.00);

SELECT * FROM Treatments;

-- 5.PatientTreatments – Treatments given to patients during appointments

CREATE TABLE PatientTreatments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    appointment_id INT,
    treatment_id INT,
    quantity INT DEFAULT 1,
    FOREIGN KEY (appointment_id) REFERENCES Appointments(appointment_id),
    FOREIGN KEY (treatment_id) REFERENCES Treatments(treatment_id)
);

INSERT INTO PatientTreatments (appointment_id, treatment_id, quantity) 
VALUES 
(1,1,1),
(1,3,2),
(2,2,1),
(3,5,1),
(4,1,1),
(5,2,2),
(6,3,1);  -- yahan tak safe hai


-- 6.Medicines – Medicine inventory

CREATE TABLE Medicines (
    medicine_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    category VARCHAR(50),
    price DECIMAL(10,2),
    stock_quantity INT DEFAULT 0
);

INSERT INTO Medicines (name, category, price, stock_quantity)
VALUES
('Paracetamol','Tablet',10.00,100),
('Amoxicillin','Antibiotic',25.00,50),
('Cough Syrup','Syrup',30.00,40),
('Vitamin C','Supplement',15.00,60),
('Insulin','Injection',200.00,30),
('Pain Relief Spray','Topical',50.00,20),
-- Add 44 more medicines like this
('Medicine7','Category1',10.00,100),
('Medicine8','Category2',20.00,80),
('Medicine9','Category3',30.00,70),
('Medicine10','Category4',40.00,60),
('Medicine50','Category5',50.00,25);

SELECT * FROM medicines;

-- 7.Suppliers – Medicine suppliers

CREATE TABLE Suppliers (
    supplier_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    contact_name VARCHAR(100),
    phone VARCHAR(15),
    email VARCHAR(100)
);

INSERT INTO Suppliers (name, contact_name, phone, email)
VALUES
('Health Supplies Co','Ramesh Kumar','900000001','supplier1@hospital.com'),
('MediCare Ltd','Sonia Singh','900000002','supplier2@hospital.com'),
('PharmaPlus','Amit Yadav','900000003','supplier3@hospital.com'),
('Wellness Meds','Neha Gupta','900000004','supplier4@hospital.com'),
('Care Pharmaceuticals','Vikram Singh','900000005','supplier5@hospital.com'),
('LifeLine Meds','Sunita Rao','900000006','supplier6@hospital.com'),
('Good Health Co','Rajeev Kumar','900000007','supplier7@hospital.com'),
('MediTrust','Seema Sharma','900000008','supplier8@hospital.com'),
('Healthy Pharma','Pooja Verma','900000009','supplier9@hospital.com'),
('SafeMed','Saurabh Singh','900000010','supplier10@hospital.com');

SELECT * FROM Suppliers;

-- 8.MedicineOrders – Medicines supplied by suppliers

DROP TABLE IF EXISTS MedicineOrders;

CREATE TABLE MedicineOrders (
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    supplier_id INT,
    medicine_id INT,
    quantity INT,
    order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (supplier_id) REFERENCES Suppliers(supplier_id),
    FOREIGN KEY (medicine_id) REFERENCES Medicines(medicine_id)
);


INSERT INTO MedicineOrders (supplier_id, medicine_id, quantity)
VALUES
(1,1,100),
(2,2,50),
(3,3,70),
(4,4,60),
(5,5,30);

SELECT * FROM MedicineOrders;

-- 9. Bills – Billing information for patients

DROP TABLE IF EXISTS Bills;

CREATE TABLE Bills (
    bill_id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT,
    appointment_id INT,
    bill_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    total_amount DECIMAL(10,2),
    payment_status ENUM('Paid','Pending') DEFAULT 'Pending',
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id),
    FOREIGN KEY (appointment_id) REFERENCES Appointments(appointment_id)
);

SHOW TABLES;  -- confirm Patients aur Appointments exist karte hain
SELECT COUNT(*) FROM Patients;
SELECT COUNT(*) FROM Appointments;



INSERT INTO Bills (patient_id, appointment_id, total_amount, payment_status)
VALUES
(1,1,5600.00,'Paid'),
(2,2,800.00,'Pending'),
(3,3,25000.00,'Paid'),
(4,4,1200.00,'Paid'),
(5,5,1500.00,'Pending'),
(6,6,700.00,'Paid');  -- <- semicolon at the end

SELECT * FROM Bills;  -- Now this will work




SELECT * FROM Bills;

-- 10. InventoryLogs – Track medicine stock changes

DROP TABLE IF EXISTS InventoryLogs;

CREATE TABLE InventoryLogs (
    log_id INT AUTO_INCREMENT PRIMARY KEY,
    medicine_id INT,
    change_type ENUM('Addition','Dispense','Return') NOT NULL,
    quantity INT,
    log_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (medicine_id) REFERENCES Medicines(medicine_id)
);
INSERT INTO InventoryLogs (medicine_id, change_type, quantity, log_date)
VALUES
(1,'Addition',100,'2025-09-01 09:00:00'),
(2,'Dispense',5,'2025-09-01 10:00:00'),
(3,'Addition',50,'2025-09-02 11:00:00'),
(4,'Dispense',3,'2025-09-02 12:00:00'),
(5,'Return',2,'2025-09-03 09:30:00'),
(6,'Addition',80,'2025-09-03 10:15:00'),
(7,'Dispense',10,'2025-09-04 11:00:00'),
(8,'Return',1,'2025-09-04 12:30:00'),
(9,'Addition',60,'2025-09-05 09:45:00'),
(10,'Dispense',7,'2025-09-05 10:30:00');

SELECT * FROM InventoryLogs;

-- 🏥 Hospital Management Advanced Business Problem Set
-- 1️⃣ Revenue & Billing Analysis

-- 1.1 Top 5 treatments by revenue

SELECT t.name AS Treatment, SUM(pt.quantity * t.cost) AS Revenue
FROM PatientTreatments pt
JOIN Treatments t ON pt.treatment_id = t.treatment_id
GROUP BY t.name
ORDER BY Revenue DESC
LIMIT 5;

-- 1.2 Revenue per doctor

SELECT d.name AS Doctor, SUM(pt.quantity * t.cost) AS Revenue
FROM Appointments a
JOIN Doctors d ON a.doctor_id = d.doctor_id
JOIN PatientTreatments pt ON a.appointment_id = pt.appointment_id
JOIN Treatments t ON pt.treatment_id = t.treatment_id
GROUP BY d.name
ORDER BY Revenue DESC;

-- 1.3 Pending bills report

SELECT p.name AS Patient, b.total_amount, b.bill_date
FROM Bills b
JOIN Patients p ON b.patient_id = p.patient_id
WHERE b.payment_status = 'Pending'
ORDER BY b.bill_date ASC;

-- 2️⃣ Inventory & Stock Management

-- 2.1 Low-stock medicines (<20 units)

SELECT name, stock_quantity
FROM Medicines
WHERE stock_quantity < 20
ORDER BY stock_quantity ASC;

-- 2.2 Total stock used per medicine

SELECT m.name, SUM(pt.quantity) AS Used
FROM PatientTreatments pt
JOIN Medicines m ON pt.treatment_id = m.medicine_id
GROUP BY m.name;

-- 2.3 Auto-stock reduce trigger


DELIMITER $$

CREATE TRIGGER ReduceStock 
AFTER INSERT ON PatientTreatments
FOR EACH ROW
BEGIN
    UPDATE Medicines
    SET stock_quantity = stock_quantity - NEW.quantity
    WHERE medicine_id = NEW.treatment_id;
END$$

DELIMITER ;

-- 2.4 Auto-reorder procedure (stock < threshold)


DELIMITER //
CREATE PROCEDURE ReorderMedicine()
BEGIN
    INSERT INTO MedicineOrders(supplier_id, medicine_id, quantity)
    SELECT 1, medicine_id, 50
    FROM Medicines
    WHERE stock_quantity < 20;
END //
DELIMITER ;

-- 3️⃣ Appointments & Operational Efficiency
-- 3.1 Total appointments per doctor per month

SELECT d.name AS Doctor, MONTH(a.appointment_date) AS Month, COUNT(*) AS TotalAppointments
FROM Appointments a
JOIN Doctors d ON a.doctor_id = d.doctor_id
GROUP BY d.name, MONTH(a.appointment_date)
ORDER BY TotalAppointments DESC;

-- 3.2 Cancelled vs completed appointments

SELECT status, COUNT(*) AS Count
FROM Appointments
GROUP BY status;

-- 3.3 Peak appointment hours

SELECT HOUR(appointment_date) AS Hour, COUNT(*) AS Appointments
FROM Appointments
GROUP BY HOUR(appointment_date)
ORDER BY Appointments DESC;

-- 4️⃣ Patient Analytics
-- 4.1 Top 5 patients by spending

SELECT p.name AS Patient, SUM(pt.quantity * t.cost) AS TotalSpent
FROM Patients p
JOIN Appointments a ON p.patient_id = a.patient_id
JOIN PatientTreatments pt ON a.appointment_id = pt.appointment_id
JOIN Treatments t ON pt.treatment_id = t.treatment_id
GROUP BY p.name
ORDER BY TotalSpent DESC
LIMIT 5;


-- 4.2 Most frequent treatments per patient

SELECT p.name AS Patient, t.name AS Treatment, COUNT(*) AS Frequency
FROM PatientTreatments pt
JOIN Appointments a ON pt.appointment_id = a.appointment_id
JOIN Patients p ON a.patient_id = p.patient_id
JOIN Treatments t ON pt.treatment_id = t.treatment_id
GROUP BY p.name, t.name
ORDER BY Frequency DESC;


-- 5️⃣ Supplier & Procurement Analysis

-- 5.1 Total medicines supplied per supplier

SELECT s.name AS Supplier, SUM(mo.quantity) AS TotalSupplied
FROM MedicineOrders mo
JOIN Suppliers s ON mo.supplier_id = s.supplier_id
GROUP BY s.name
ORDER BY TotalSupplied DESC;

-- 5.2 Supplier reliability (deliveries count)

SELECT s.name AS Supplier, COUNT(*) AS DeliveryCount
FROM MedicineOrders mo
JOIN Suppliers s ON mo.supplier_id = s.supplier_id
GROUP BY s.name
ORDER BY DeliveryCount DESC;

-- 5.3 Cost optimization – cheapest medicine per category

SELECT category, name, price
FROM Medicines m
WHERE price = (SELECT MIN(price) FROM Medicines WHERE category = m.category);

-- 6️⃣ Automation & Stored Procedures

-- 6.1 Generate bill automatically after appointment

DELIMITER //
CREATE PROCEDURE GenerateBill(IN app_id INT)
BEGIN
    DECLARE total DECIMAL(10,2);
    SELECT SUM(t.cost * pt.quantity) INTO total
    FROM PatientTreatments pt
    JOIN Treatments t ON pt.treatment_id = t.treatment_id
    WHERE pt.appointment_id = app_id;
    
    INSERT INTO Bills(patient_id, appointment_id, total_amount, payment_status)
    SELECT patient_id, appointment_id, total, 'Pending'
    FROM Appointments
    WHERE appointment_id = app_id;
END //
DELIMITER ;

-- 6.2 Daily revenue view]

CREATE VIEW DailyRevenue AS
SELECT DATE(bill_date) AS bill_day, SUM(total_amount) AS revenue
FROM Bills
GROUP BY DATE(bill_date);


-- 8️⃣ Inventory Logs & Auditing
-- 8.1 Track medicine additions and dispenses

SELECT m.name, il.change_type, SUM(il.quantity) AS TotalQuantity
FROM InventoryLogs il
JOIN Medicines m ON il.medicine_id = m.medicine_id
GROUP BY m.name, il.change_type;


-- 8.2 Last 5 stock changes per medicine

SELECT m.name, il.change_type, il.quantity, il.log_date
FROM InventoryLogs il
JOIN Medicines m ON il.medicine_id = m.medicine_id
ORDER BY il.log_date DESC
LIMIT 5;

-- 📝 Challenge 1

-- Find top 5 treatments generating highest revenue

SELECT 
    t.name AS Treatment,
    SUM(pt.quantity * t.cost) AS TotalRevenue
FROM PatientTreatments pt
JOIN Treatments t 
    ON pt.treatment_id = t.treatment_id
GROUP BY t.name
ORDER BY TotalRevenue DESC
LIMIT 5;

-- Challenge 2: Calculate revenue generated by each doctor.

SELECT 
    d.name AS Doctor,
    SUM(pt.quantity * t.cost) AS TotalRevenue
FROM Appointments a
JOIN Doctors d 
    ON a.doctor_id = d.doctor_id
JOIN PatientTreatments pt 
    ON a.appointment_id = pt.appointment_id
JOIN Treatments t 
    ON pt.treatment_id = t.treatment_id
GROUP BY d.name
ORDER BY TotalRevenue DESC;

    
    -- Challenge 3: Show all patients with pending bills in ascending order of bill date.
    
SELECT 
    p.name AS PatientName,
    b.total_amount AS BillAmount,
    b.payment_status AS Status,
    b.bill_date
FROM Bills b
JOIN Patients p 
    ON b.patient_id = p.patient_id
WHERE b.payment_status = 'Pending'
ORDER BY b.bill_date ASC;


-- 📌 Section 2: Inventory & Stock


SELECT 
    name AS MedicineName, 
    stock_quantity AS CurrentStock
FROM Medicines
WHERE stock_quantity < 20;

-- Challenge 5: Find total usage of each medicine across treatments.


SELECT 
    m.name AS MedicineName, 
    SUM(pt.quantity) AS TotalUsed
FROM PatientTreatments pt
JOIN Medicines m ON pt.treatment_id = m.medicine_id
GROUP BY m.name;


-- Challenge 6: Create a trigger to automatically reduce stock after a treatment.

DELIMITER $$

CREATE TRIGGER ReduceMedicineStock
AFTER INSERT ON PatientTreatments
FOR EACH ROW
BEGIN
    UPDATE Medicines
    SET stock_quantity = stock_quantity - NEW.quantity
    WHERE medicine_id = NEW.treatment_id;
END$$

DELIMITER ;


INSERT INTO PatientTreatments (appointment_id, treatment_id, quantity)
VALUES (101, 1, 5);

SELECT * FROM PatientTreatments;

-- Challenge 7: Create a stored procedure to auto-generate medicine order when stock < 20.

DELIMITER $$

CREATE PROCEDURE AutoGenerateMedicineOrder()
BEGIN
    INSERT INTO Orders (med_id, order_date, quantity, status)
    SELECT m.medicine_id, NOW(), 50, 'Pending'
    FROM Medicines m
    WHERE m.stock_quantity < 20
      AND m.medicine_id NOT IN (
          SELECT o.med_id
          FROM Orders o
          WHERE o.status = 'Pending'
      );
END$$

DELIMITER ;


SHOW COLUMNS FROM Orders;

CALL AutoGenerateMedicineOrder();

-- 📌 Section 3: Appointments & Efficiency
-- Challenge 8, you want the total number of appointments per doctor per month.
USE projectdb;

SELECT 
    d.name AS Doctor,
    DATE_FORMAT(a.appointment_date, '%Y-%m') AS Month,
    COUNT(*) AS AppointmentCount
FROM Appointments a
JOIN Doctors d ON a.doctor_id = d.doctor_id
GROUP BY d.name, DATE_FORMAT(a.appointment_date, '%Y-%m')
ORDER BY d.name, Month;

-- Challenge 9, you just need the counts of Completed and Cancelled appointments.

SELECT 
    status,
    COUNT(*) AS TotalCount
FROM Appointments
WHERE status IN ('Completed', 'Cancelled')
GROUP BY status;


    -- Challenge 10, you want the busiest appointment hour (the hour of the day with the most appointments).
    

SELECT 
    HOUR(appointment_date) AS HourOfDay,
    COUNT(*) AS AppointmentCount
FROM Appointments
GROUP BY HOUR(appointment_date)
ORDER BY AppointmentCount DESC
LIMIT 1;

-- 📌 Section 4: Patient Insights
-- Challenge 11, you want the top 5 patients by total spending (based on their treatments & bills).

SELECT 
    p.name AS Patient,
    SUM(pt.quantity * t.cost) AS TotalSpending
FROM Patients p
JOIN Appointments a 
    ON p.patient_id = a.patient_id
JOIN PatientTreatments pt 
    ON a.appointment_id = pt.appointment_id
JOIN Treatments t 
    ON pt.treatment_id = t.treatment_id
GROUP BY p.name
ORDER BY TotalSpending DESC
LIMIT 5;

--  For Challenge 12, you want to find the treatment each patient receives most frequently.

SELECT 
    t1.PatientName,
    t1.TreatmentName,
    t1.Frequency
FROM (
    SELECT 
        p.name AS PatientName,
        t.name AS TreatmentName,
        COUNT(*) AS Frequency,
        ROW_NUMBER() OVER (PARTITION BY p.patient_id ORDER BY COUNT(*) DESC) AS rn
    FROM PatientTreatments pt
    JOIN Appointments a ON pt.appointment_id = a.appointment_id
    JOIN Patients p ON a.patient_id = p.patient_id
    JOIN Treatments t ON pt.treatment_id = t.treatment_id
    GROUP BY p.patient_id, t.treatment_id
) t1
WHERE t1.rn = 1
ORDER BY t1.PatientName;

--  📌 Section 5: Supplier & Procurement

SELECT 
    s.name AS SupplierName,
    SUM(mo.quantity) AS TotalSupplied
FROM MedicineOrders mo
JOIN Suppliers s 
    ON mo.supplier_id = s.supplier_id
GROUP BY s.name
ORDER BY TotalSupplied DESC;


-- Challenge 14 me aapko har supplier ke deliveries count ke basis pe rank karna hai.
SELECT 
    s.name AS SupplierName,
    COUNT(*) AS DeliveryCount
FROM MedicineOrders mo
JOIN Suppliers s 
    ON mo.supplier_id = s.supplier_id
GROUP BY s.name
ORDER BY DeliveryCount DESC;

-- Challenge 15 me aapko har medicine category me sabse sasti medicine dikhani hai.

SELECT 
    m.category,
    m.name AS MedicineName,
    m.price
FROM Medicines m
WHERE m.price = (
    SELECT MIN(price)
    FROM Medicines
    WHERE category = m.category
)
ORDER BY m.category;

-- 📌 Section 6: Automation

-- Challenge 16 me aapko automatic bill generate karna hai appointment ke liye.

DELIMITER //

CREATE PROCEDURE GenerateBill(IN app_id INT)
BEGIN
    DECLARE total DECIMAL(10,2);

    -- Total amount calculate karo treatments ke liye
    SELECT SUM(pt.quantity * t.cost) INTO total
    FROM PatientTreatments pt
    JOIN Treatments t ON pt.treatment_id = t.treatment_id
    WHERE pt.appointment_id = app_id;

    -- Bill insert karo Bills table me
    INSERT INTO Bills(patient_id, appointment_id, total_amount, payment_status)
    SELECT patient_id, appointment_id, total, 'Pending'
    FROM Appointments
    WHERE appointment_id = app_id;
END //

DELIMITER ;

-- Challenge 17: Create a view for daily revenue.

SELECT 
    DATE(bill_date) AS RevenueDate,
    SUM(total_amount) AS TotalRevenue
FROM Bills
GROUP BY DATE(bill_date)
ORDER BY RevenueDate;

-- 📌 Section 7: Advanced Analytics (Window Functions)

-- 2️⃣ Step 1: Calculate monthly revenue per doctor

SELECT 
    d.name AS Doctor,
    DATE_FORMAT(a.appointment_date, '%Y-%m') AS Month,
    SUM(pt.quantity * t.cost) AS Revenue
FROM Appointments a
JOIN Doctors d ON a.doctor_id = d.doctor_id
JOIN PatientTreatments pt ON a.appointment_id = pt.appointment_id
JOIN Treatments t ON pt.treatment_id = t.treatment_id
GROUP BY d.name, DATE_FORMAT(a.appointment_date, '%Y-%m');

-- 3️⃣ Step 2: Rank doctors by revenue in each month

WITH MonthlyDoctorRevenue AS (
    SELECT 
        d.name AS Doctor,
        DATE_FORMAT(a.appointment_date, '%Y-%m') AS Month,
        SUM(pt.quantity * t.cost) AS Revenue
    FROM Appointments a
    JOIN Doctors d ON a.doctor_id = d.doctor_id
    JOIN PatientTreatments pt ON a.appointment_id = pt.appointment_id
    JOIN Treatments t ON pt.treatment_id = t.treatment_id
    GROUP BY d.name, DATE_FORMAT(a.appointment_date, '%Y-%m')
)
SELECT *
FROM (
    SELECT *,
           ROW_NUMBER() OVER (PARTITION BY Month ORDER BY Revenue DESC) AS `Rank`
    FROM MonthlyDoctorRevenue
) AS Ranked
WHERE `Rank` <= 3
ORDER BY Month, `Rank`;

-- Hume patients ko unke total spending ke hisaab se rank karna hai:

-- 3️⃣ Step 1: Total spending per patient

SELECT 
    p.name AS Patient,
    SUM(b.total_amount) AS TotalSpent
FROM Patients p
JOIN Bills b ON p.patient_id = b.patient_id
GROUP BY p.name;

-- 4️⃣ Step 2: Rank patients by spending

SELECT 
    Patient,
    TotalSpent,
    RANK() OVER (ORDER BY TotalSpent DESC) AS `Rank`
FROM (
    SELECT 
        p.name AS Patient,
        SUM(b.total_amount) AS TotalSpent
    FROM Patients p
    JOIN Bills b ON p.patient_id = b.patient_id
    GROUP BY p.name
) AS PatientSpending
ORDER BY `Rank`;
-- 📌 Section 8: Inventory Logs & Auditing

SELECT 
    m.name AS MedicineName,
    i.change_type AS ChangeType,
    SUM(i.quantity) AS TotalQuantity
FROM medicines m
JOIN inventorylogs i
    ON m.medicine_id = i.medicine_id
GROUP BY m.name, i.change_type
ORDER BY m.name, i.change_type;


-- Challenge 21 is simpler. Humko last 5 stock changes dikhane hain most recent date ke hisaab se.

SELECT 
    m.name AS MedicineName,
    i.change_type AS ChangeType,
    i.quantity AS Quantity,
    i.change_date AS ChangeDate
FROM medicines m
JOIN inventorylogs i
    ON m.medicine_id = i.medicine_id
ORDER BY i.change_date DESC
LIMIT 5;

