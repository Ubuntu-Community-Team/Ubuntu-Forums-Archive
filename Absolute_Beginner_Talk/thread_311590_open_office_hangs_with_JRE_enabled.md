---
title: "open office hangs with JRE enabled"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by rajeev1204 on 2006-12-03
hi

i have dapper 6.06 64 bit. open office hangs when i use JRE. i have to disable java to run it . but i cant use the wizards option if i do that.
java version is blackdown .

is it a known issue.


please help

---

### Post by 56phil on 2006-12-03
I don't have this problem.

32-bit, Edgy, JDK 1.5.

I not familiar with blackdown. What is it, please.

---

### Post by rajeev1204 on 2006-12-03
hi

 thanks for the reply.

blackdown j2re 1.4  is default java version installed in dapper 64 bit -( i think) 
u r using 32 bit edgy so u wont have issues with java. open office is still a  32 bit application so i think that is why it behaves so in 64 bit dapper.

regards
rajeev

---

### Post by 56phil on 2006-12-03
Hi, 

I'm using 32-bit Edgy because I have a 32-bit system. Have you considered upgrading to Edgy? It has a newer version of Open Office.

---

### Post by rajeev1204 on 2006-12-03
hi

ohh i just installed dapper so i think i will get used to it first before upgrading to edgy. but thanks anyways.

also i want to know is i can install 32 bit ubuntu on my AMD 64 like XP.

btw , is edgy any better ?


regards

rajeev

---

### Post by 56phil on 2006-12-03
Yes, I hear that you can run 32-bit on an AMD 64-bit machine.

Edgy has a newer kernel, version of Open Office, etc. Some people are so unhappy with it that they have returned to Dapper, but I'm happy with it.

---

### Post by rajeev1204 on 2006-12-03
hi

thanks for the reply.

wish u all the best with edgy. i may upgrade after a few months. lets see how things go with dapper .


regards

rajeev


P.S iam using open office with java disabled.but thats ok for now.

---

### Post by dubrict on 2006-12-04
I was just having this problem.  I have 64-bit ubuntu, and it took over a minute to load openoffice.  Search in synaptic for the package "j2re1.4" and install it.  This will install the Blackdown virtual machine.  Then, load up openoffice and go to the options and re-enable the use of java.
The list of virtual machines should now have blackdown listed.  Select it and restart openoffice.
Hope this helps.

---

### Post by rajeev1204 on 2006-12-04
hi

i have installed j2re 1.4 and openoffice hangs with that enabled. when i go to tools/options/java it takes a lot of time to show which version i have installed and it does not show j2re. it lists some gcj free software version. . if i enable it , openoffice just wouldnt run properly. hangs every time.:( 


iam currently running without java .and it runs fine. but i lose a lot of the  functionality in office.


regards

rajeev
dapper 64 bit user

---

### Post by dubrict on 2006-12-05
That's strange, it solved the problem in mine... loading time went from over a minute to under 3 seconds with it.
I'm sorry, I don't know what to tell you then.  All I can think of is that I also used automatix2 to install java, but that was before experiencing my slowness in openoffice.  Maybe with both installed it will speed up.  I doubt it though.

Also, I'm using edgy so that may have to do with the difference.  I'm sure it's better at handling 32-bit applications like java.
Maybe you should upgrade, it's really not that hard.  All you have to do is open your /etc/apt/sources.list file and change all the package sources to say "edgy" instead of "dapper."  Then just update all your packages.

Just be wary that there's people on here who have had some mis-functionality when doing that.  And sorry, I didn't notice you said you already had j2re1.4 installed.

---

### Post by rajeev1204 on 2006-12-05
hi dubrict,

i did a fresh install of ubuntu ( for an unrelated problem !) , and i still find this problem with open office.it hangs all the time when i use wizards, etc .  Also the sun-java 5 bin package in my repos is always broken . do  u  have a smilar problem? 


regards

rajeev

---

### Post by Perfect Storm on 2006-12-05
I don't know if this works on 64-bit, but you could give it a try: [http://ubuntuforums.org/showthread.php?t=311031&highlight=java](http://ubuntuforums.org/showthread.php?t=311031&highlight=java)

---

### Post by rajeev1204 on 2006-12-05
Hi 

i found something interesting

i typed version -java in terminal and it gave me j2re 1.4.2 build blackdown

when i uninstall blackdown j2re 1.4 it tells me java version now is gcj 1.4 free software foundation.

under tools/options/java openoffice shows this free software foundation version. 

is there a way to change this to the blackdown j2re build cos i think that could be a solution

Also , when i try to uninstall gcj free software foundation java, it wants to uninstall entire office suite


regards

rajeev

---

### Post by rajeev1204 on 2006-12-05
hi

someone please help me with this. 

this time i tried installing the 32 bit JRE ia 32 sun java  and open office shows this version in tools/options. but it still hangs all the time.

it seems to have trouble detecting java . takes  a long time to show available java versions in tools/options.](*,)

---

### Post by dubrict on 2006-12-05
to install the sun-java 5 package, you should use automatix2.  Instructions for installing that should be here:  [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

After looking into it more, that's not the problem, as the blackdown version should be just fine.  What version of openOffice are you using?

---

### Post by rajeev1204 on 2006-12-05
hi

iam using openoffice 2.0.2 . i found the 32 bit java in the repos so i tried that . anyway i will try automatix if that helps.

i found on google that other 64 bit distros also have a similar problem . it hangs at tools/options/java

regards

rajeev

---

