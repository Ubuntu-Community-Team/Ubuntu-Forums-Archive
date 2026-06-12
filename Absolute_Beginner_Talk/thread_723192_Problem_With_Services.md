---
title: "Problem With Services"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by RAJESHKSV on 2008-03-13
I HAD A PROBLEM WITH SERVICES..I OPENED SERVICES THR SYSTEM->ADMINISTARTION->SERVICES AND I REMOVED SOME OF THEM BEING SURE THAT EVEN IF I STOP THE MAIN SERVICES,THEY WILL BE STARTED AGAIN ON RESTART..BUT IT DIDNT HAPPEN LIKE THAT...I DONNO WHICH SERVICE I UNCHECKED  BUT AFTER THAT I AM UNABLE TO OPEN THAT SERVICES WINDOW AGAIN...

IT IS SAYING

THE CONFIGURATION COULDNOT BE LOADED
YOU ARE NOT ALLOWED TO ACCESS SYSTEM CONFIGURATION

EVEN WHEN I RESTARTED THE SYSTEM IT IS SAYING SAME 
AND IT IS ALSO SAYING (IN THE BEGINNING A SMALL DIALOG BOX IS OPENING DISPLAYING)

INTERNAL SYSTEM ERROR
FAILED TO INITIALISE HAL!!

DUE TO THAT ( I THNK MANY OPTIONS DISAPPEARED INCLUDING HIBERNATE,SLEEP WHICH WILL COME WHEN I CLICK QUIT OPTION).SO I WANNA RESET ALL SERVICES TO DEFAULT
SO THAT REQUIRED SERVICES WILL BE STARTED AGAIN...IS THERE ANY RELATION BETWEEN SERVICES AND ABOVE SYMPTOMS???PLZ HELP:confused:

---

### Post by RAJESHKSV on 2008-03-13
sry for posting this post...after i had posted i checked in this community and found the solution....:)

 1) Run the following command at the terminal:-
 
 
Code:
sudo /etc/init.d/dbus start
2) Then run services-admin and enable the System Communication Bus (dbus).

my problem is solved...once again it is proved UBUNTU and its community rocks!!!!!!:guitar:

---

### Post by RAJESHKSV on 2008-03-14
Oops..the problem is not completely solved yet!!!I I searched in ubuntu forums and found the        soultion but its not working completely ....When I entered the above,everything is fine,but it is only upto that session.When I restart it again , services window is  opening but still   some services like hibernate,sleep are not working...Also the window 

"Internal error:failed to initialise hal" 

is still coming after every reboot...Everytime I switch on my lap, I have to stop the system communication bus(dbus) and restart it again(through the above command)

...then hibernate and sleep are working...Is there a complete solution to this problem????

---

