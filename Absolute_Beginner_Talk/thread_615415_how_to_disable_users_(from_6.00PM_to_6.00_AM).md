---
title: "how to disable users (from 6.00PM to 6.00 AM)"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-11-17
i want to create a user account(unprivilaged).it should be enabled at(from 6.00AM to 6.00 PM only)  per day.

any idea ?

---

### Post by arkangel on 2007-11-17
you can create a script and put it in cron.hourly   "/etc/cron.hourly"

in this script ask :
> 

if 6:00 then 
    usermod  -U  user
else if 18:00 then 
    usermod -L user
end if  

 

this is pseducode script -- you have to  make it bash --

usermod   -U unlocks the password for the user , and -L  locks her password

---

### Post by arkangel on 2007-11-17
you can start with 

%date "+%I"

it returns the hour 
and your script   would look like this 

> 
#!/bin/bash

if [  %date "+%I" = '06' ]; then 
    usermod -U user 

elif [  %date "+%I" = '18' ]; then
   usermod -L user

fi



you have to check  the syntactic   of the if bash (good simple tutorial in google) and the test expression "[ ]"

---

### Post by arkangel on 2007-11-17
ok  this should work , put  this bash script  in  /etc/cron.hourly  ,  make it executable  and owned by root 

> 
#!/bin/bash

HOUR=$(date "+%I")

if [ $HOUR = '06' ]; then
      $(usermod -U [USER])
elif [ $HOUR = '18' ]; then
      $(usermod -L [USER])
fi

 

[USER]  replace with the user name

---

### Post by mokkai on 2007-11-17
thank you very much, 
now i am going to try this.

---

### Post by adam.tropics on 2007-11-17
I thought usermod -L locked the user out from being able to log in. What if the user is already logged in?

---

### Post by mokkai on 2007-11-17
> **adam.tropics said:**
> I thought usermod -L locked the user out from being able to log in. What if the user is already logged in?

yes ,What if the user is already logged in?

the script is not running per hour.

and if we killed that user_name at 18th hour ,then suddenly the user_name session halt(so loss of data occured) .

Is there any other idea to show a message to the user (so she can ready to logoff like save documents ,etc....)  ,
and after 1 minites the session should be halt smoothly (like as ordinary logoff  process)

---

### Post by brennydoogles on 2007-11-17
> **mokkai said:**
> yes ,What if the user is already logged in?

the script is not running per hour.

and if we killed that user_name at 18th hour ,then suddenly the user_name session halt(so loss of data occured) .

Is there any other idea to show a message to the user (so she can ready to logoff like save documents ,etc....)  ,
and after 1 minites the session should be halt smoothly (like as ordinary logoff  process)

well, you could automate a system restart in the script with ```
sudo shutdown -hr 18:00
``` (please check my syntax on the time, which should be 6pm), and then the user would be able to log on afterwards, and then another restart after the time is up. The user SHOULD recieve a prompt several times before the system shuts down, but I have only seen the prompt when a terminal window is open, so I am not sure how it would work otherwise. I hope that helps!!

---

### Post by mokkai on 2007-11-17
> **brennydoogles said:**
> well, you could automate a system restart in the script with ```
sudo shutdown -hr 18:00
``` (please check my syntax on the time, which should be 6pm), and then the user would be able to log on afterwards, and then another restart after the time is up. The user SHOULD recieve a prompt several times before the system shuts down, but I have only seen the prompt when a terminal window is open, so I am not sure how it would work otherwise. I hope that helps!!

thank you for reply
but the System is Server , so if shutdown then others will be affect...
actually i want to give that permission to unprevilaged users only...

---

### Post by arkangel on 2007-11-18
well you can try with  adding lines to the script

for example in the part  if "18h" play with these lines

> 
if  ( HOUR=06 ) then 
....
elif ( HOUR=18 ) then
lock the user ...
[INDENT]  if [ $(who  | grep  [USER] | wc -l) -gt 0 ]; then
      "warn the user "
       " log out the user  giving her some time for saving   her work  " 
  fi[/INDENT] 

fi 



if the user has logged  in ,  this command   $(who  | grep  [USER] | wc -l)  will give any value bigger than 1

to kill the user applications,  you have first to get a formatted output  from ps command . You might read the man page for ps, for example:
 
% ps -u [USER]  -o "some format "  |   kill -[n] ; where  n is a suitable   number for stopping the processes,  
somehow you how to figure out  how the "some format "  will return  a list of pid numbers , for instances  "1234 12123"
so 
%kill -5  1234 12123
will disconnect the user and kill all her processes 

%man kill  
will also help :)

sometimes you want to disconnect the user  but  you dont want to stop  all her processes , for example all her nohup processes can continue 
> 
%ps -u [USER]| grep bash

assuming her shell is bash ..   well  you have to play around it

---

