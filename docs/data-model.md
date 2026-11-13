# CargoFlow — Proposed Data Model

**Development stage:** TRL 2 — Technology Concept Formulation.

## 1. Purpose

This document outlines the proposed information structure required to support CargoFlow's cargo visibility and exception-management functions.

## 2. Core Data Entities

### A. Shipment

Represents an individual cargo movement.

Proposed fields:
- Shipment ID
- Container number
- Bill of lading reference
- Cargo owner or authorised customer ID
- Origin and destination
- Expected arrival and delivery dates
- Current shipment status

### B. Cargo Event

Records an activity or update during the shipment journey.

Proposed fields:
- Event ID
- Shipment ID
- Event type
- Event description
- Event timestamp
- Reporting source
- Verification status

### C. Stakeholder

Represents an organisation or authorised participant involved in the cargo journey.

Proposed fields:
- Stakeholder ID
- Organisation name
- Stakeholder category
- Contact or authorised user reference
- Access permissions

### D. Milestone

Represents an expected event or stage in the shipment journey.

Proposed fields:
- Milestone ID
- Shipment ID
- Milestone name
- Expected completion time
- Actual completion time
- Milestone status

### E. Exception

Records a deviation or unresolved operational issue.

Proposed fields:
- Exception ID
- Shipment ID
- Related milestone
- Exception category
- Description
- Date identified
- Severity
- Resolution status

### F. Action Record

Tracks the next required action relating to an exception.

Proposed fields:
- Action ID
- Exception ID
- Responsible stakeholder
- Required action
- Action deadline
- Action status
- Resolution timestamp

## 3. Relationships Between Data Entities

- One shipment can have multiple cargo events.
- One shipment can have multiple milestones.
- A missed or abnormal milestone can generate an exception for review.
- An exception can have one or more associated action records.
- Stakeholders can be associated with multiple shipments and actions.

## 4. Data Reliability

CargoFlow is designed to preserve the source and timestamp of recorded events.

Information will be classified according to its verification status so that users can distinguish confirmed updates from unverified submissions.

Conflicting or incomplete information should be flagged for review rather than automatically treated as confirmed.

## 5. Data Protection

The proposed platform will use authorised access, role-based permissions and appropriate safeguards to protect commercially sensitive shipment information.

## 6. Development Objective

This proposed data model will guide proof-of-concept development and subsequent validation of CargoFlow's shipment timeline and exception-management workflows.
