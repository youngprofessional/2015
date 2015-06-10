Lufthansa Systems Hungária Kft. - Test for Software Developers
======================================

Please create a complete software package which fulfils the specification below. In case you would like to pursue a career in software testing, then you should create a comprehensive test plan for this software module.

In order to facilitate the understanding, you should include code comments, software documentation, build scripts and test cases as you feel appropriate.

You can choose from the following languages: Java, Javascript, C/C++, Scala. You may use any mainstream framework / library for the implementation, only requirement is that the code compiles and runs according to the specification.‎

You will have 1 week to provide a solution. You might submit partial solutions in case you think it can be evaluated.

Specification
-------------

### Maintenance Control

Aircrafts are well utilized machinery. In order to keep them safely operating for more than 20 yrs, they need constant maintenance. Maintenance events (or checks) as all other duties of an aircraft must be planned, executed and audited. 

Your task is to create a software which does the auditing of the checks. As checks are reoccouring, they all define a certain pattern. This might include the number take-off/landing cycles, flight hours or calendar days since the last check. 

The input of the application includes a schedule with aircrafts and their flight legs, and the planned/executed checks. Each leg has a status from the following list:

- SKD - Scheduled
- DEP - Departed
- ARR - Arrived
- CNL - Cancelled
- RTR - Return to ramp
- DIV - Diverted

Also, legs includes various timestamps:
- Scheduled Departure Time
- Scheduled Arrival Time
- Actual Departure Time
- Actual Arrival Time
- Take-off Time
- Landing Time

## Checks

The checks will be defined as an input file of the application. Each check will have a short-name and triggering events. In case of multiple triggers, it is enough to have only one of them to trigger a violation.

Some checks include others. eg. "B" check is a more complete check, it will include "A" check. So in case "B" check is performed, the "A" check is also considered performed.

## Flight hours

The amount of flight hours is to be calculated is dependent on the status of the leg:

  - Scheduled legs shall be calculated using the scheduled times. 
  - Diverted and Departured legs shall use the departure time and the scheduled arrival
  - Arrived legs shall use the actual times
  - RTR and Cancelled legs should be skipped

## Cycles

Cancelled and RTR legs should be skipped, all other legs will count as one cycle.

### Runtime

The maintenance control application need to load the masterdata and the schedule. It will need to perform the auditing of the schedule, which involves in listing the violations found.

**Input of the program:**
   - name of the check file (see masterdata.xml)
   - name of the schedule file (see schedule.xml)

**Output of the program:**

The list of violations.

**Example:**   
```
"A" CHECK VIOLATION FOR LEG LH400 FRA-JFK 2015-07-11: 204 cycles at landing (limit: 200) 
"B" CHECK VIOLATION FOR LEG LH416 FRA-IAD 2015-07-11: 249 flight hours at landing (limit: 240)
```
(please note that the above example is not the expected output of the example input file.)
