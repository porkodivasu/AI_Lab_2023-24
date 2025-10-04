# Ex.No: 11  Planning –  Monkey Banana Problem
### DATE:04-10-2025                                                                            
### REGISTER NUMBER : 212223060199
### AIM: 
To find the sequence of plan for Monkey Banana problem using PDDL Editor.
###  Algorithm:
Step 1:  Start the program <br> 
Step 2 : Create a domain for Monkey Banana Problem. <br> 
Step 3:  Create a domain by specifying predicates. <br> 
Step 4: Specify the actions GOTO, CLIMB, PUSH-BOX, GET-KNIFE, GRAB-BANANAS in Monkey Banana problem.<br>  
Step 5:   Define a problem for Monkey Banana problem.<br> 
Step 6:  Obtain the plan for given problem.<br> 
Step 7: Stop the program.<br> 
### Program:
```
(define (domain monkey)	       
  (:requirements :strips)
   (:constants monkey box knife bananas glass waterfountain)
   (:predicates (location ?x)
	       (on-floor)
	       (at ?m ?x)
	       (hasknife)
	       (onbox ?x)
	       (hasbananas)
	       (hasglass)
	       (haswater))
   ;; movement and climbing
  (:action GO-TO
	     :parameters (?x ?y)
	     :precondition (and (location ?x) (location ?y) (on-floor) (at monkey ?y))
	     :effect (and (at monkey ?x) (not (at monkey ?y))))
   (:action CLIMB
	     :parameters (?x)
	     :precondition (and (location ?x) (at box ?x) (at monkey ?x))
	     :effect (and (onbox ?x) (not (on-floor))))
   (:action PUSH-BOX
	     :parameters (?x ?y)
	     :precondition (and (location ?x) (location ?y) (at box ?y) (at monkey ?y) 
				 (on-floor))
	     :effect (and (at monkey ?x) (not (at monkey ?y))
			   (at box ?x)    (not (at box ?y))))
  ;; getting bananas
  (:action GET-KNIFE
	     :parameters (?y)
         :precondition (and (location ?y) (at knife ?y) (at monkey ?y))
	     :effect (and (hasknife) (not (at knife ?y))))
  (:action GRAB-BANANAS
	     :parameters (?y)
	     :precondition (and (location ?y) (hasknife) 
                                 (at bananas ?y) (onbox ?y))
	     :effect (hasbananas))
  ;; getting water
  (:action PICKGLASS
	     :parameters (?y)
	     :precondition (and (location ?y) (at glass ?y) (at monkey ?y))
	     :effect (and (hasglass) (not (at glass ?y))))
  (:action GETWATER
	     :parameters (?y)
	     :precondition (and (location ?y) (hasglass)
				 (at waterfountain ?y)
				 (at monkey ?y)
				 (onbox ?y))
	     :effect (haswater)))
```

### Input :
```
(define (problem pb1)
(:domain monkey)
(:objects p1 p2 p3 p4 bananas monkey box knife) (:init (location p1)
 (location p2)
(location p3)
(location p4)
(at monkey p1)
(on-floor)
(at box p2)
(at bananas p3)
(at knife p4) )
(:goal (and (hasbananas)))
)
```

### Output/Plan:
<img width="1252" height="710" alt="Screenshot 2025-10-04 073322" src="https://github.com/user-attachments/assets/15a3e9df-4738-4bf0-87c4-4ae0852f19de" />

<img width="1251" height="523" alt="Screenshot 2025-10-04 073348" src="https://github.com/user-attachments/assets/10e9a1b8-402b-40d8-8bc7-ab55bdc45116" />

<img width="1235" height="547" alt="Screenshot 2025-10-04 073403" src="https://github.com/user-attachments/assets/2d2d3d8a-06d8-4d21-821c-c4920be8530e" />

<img width="1231" height="664" alt="Screenshot 2025-10-04 073447" src="https://github.com/user-attachments/assets/f578c377-055f-4d81-beff-1ecedc78c52b" />

<img width="1237" height="520" alt="Screenshot 2025-10-04 073502" src="https://github.com/user-attachments/assets/e73efb97-1206-4481-8a6c-48a5cafa1c14" />

<img width="1277" height="549" alt="Screenshot 2025-10-04 073716" src="https://github.com/user-attachments/assets/c24a826d-8bc6-4ff0-a846-e3932b3d24fd" />


### Result:
Thus the plan was found for the initial and goal state of given problem.
