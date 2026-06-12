---
title: "kino is not doing it anymore"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-08-21
deleted the user account in which kino worked alrite, 


now  kino won't start and i can't get it to work under any of the other  accounts 
:confused:


i saw the link to download a newer version, but how do i delete this one and do i just download the newer version in the thread link.

---

### Post by firedancer on 2007-08-21
ok , i decided to download the newer version as suggested , so i did 1.1.1 and then saw it wasn't working either (in the thread)

so i decided to download the older version 1.0. but it won't install because the  installer wont do an older version 


how to remove 1.1.1 and get the 1.0.0 version so i can at least try that one








i really don't know why i messed it up it was good man:(  


i don't want to sound silly , but help pls

---

### Post by firedancer on 2007-08-21
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0
>>> iec61883Reader::StartThread on port 0


tis is what my terminal gives me ,but no image , does 1.0.0 work good , cananyone tell me how to get it 

thnx

---

### Post by Amazona aestiva on 2007-08-22
First uninstall the currently configured kino with this: (if kino is installed)
```
sudo apt-get remove kino
```
Than see this:[http://ubuntuforums.org/showthread.php?t=529759]("http://ubuntuforums.org/showthread.php?t=529759")

---

### Post by firedancer on 2007-08-22
was hoping you would show up Amazona aestiva, thank god !



ok, then i wasn't sure about the removal part.


i'll get going then . :)

---

### Post by firedancer on 2007-08-22
i'll post later how it went , need to finish some report (study), ok 

but i removed 9.? and  installed 1.0.0.  already,   later 


:)

---

### Post by firedancer on 2007-08-22
out stupid curiousity i installed the plugins , which i believe i already had and , i had bunch of errors, this is going from bad to worst 

what now ?


i did an uninstall because i went to rpo for something and did a autoremove , saw that kino was leabing with plugins , so then i strarted kino in terminla and no kino !, so i startes the plugins before installing kino 1.0.0 , but now i dont know what to do ???

messing -up my system who sent me !!

---

### Post by firedancer on 2007-08-22
BUMP 



](*,):cry::-&




i'm not going to touch .........it until , well i'm afraid if i remove all those plugins that i'll remove all i already installed 

i just am not sure what 's the best approach for a situation like this ...

---

### Post by firedancer on 2007-08-22
well, no kino then ...

---

### Post by firedancer on 2007-08-22
just gonna reinstall kino then 


ooh by the power of ubuntu >>>>>>>>>>>oOOOOOOO000))))))>

---

### Post by Amazona aestiva on 2007-08-23
Bad luck:(...
Have you tried Kino 1.1.1?
[http://www.getdeb.net/app.php?name=Kino]("http://www.getdeb.net/app.php?name=Kino")

---

### Post by firedancer on 2007-08-23
just finished  cleaning up the mess, ppff

now i'm gonna do 1.0.0 first , wasn't able to

busy

---

### Post by firedancer on 2007-08-24
can it also be a cpu problem still have this weak celeron which i need to replace for a pentium 4

cause kino would work capturing would go only the program would run slow , stopping it would wait awhile and then stop , etc, etc

cause i suddenly got it working , but this doesn't want  repeat itself ,   after deleting the user account in which i had it setup and working

:confused:

---

### Post by Amazona aestiva on 2007-08-24
Have no idea sorry...
I would reinstall Ubuntu if Kino is needed very much...

---

### Post by firedancer on 2007-08-24
well , gonna try rmmod eth1394 or rmmod ieee1394 , read in some thread that it can be the solution 

if i still have no luck 

i'll wait on the cpu  and gutsy to see if i get it going again 



but thnx anyway


yeah , i need it but , rite now i have alot of work need to graduate in march so january all the work and projects have to be finished  , after that i'll do some mulltimedia art stuff including film, learn some more python, etc.,etc..  

and i know there 's a way ! thanx  anyway !

:)

---

### Post by firedancer on 2007-08-27
the good part :
well, after trying (accept reinstalling ubuntu)  , only with gksudo, kino strarts and av/c is enabled (never was able to get that working) , and works perfectly , 

accept for one major problem

the bad :
commenting gksudo let's me only save in my root file , and i can't even delete the files afterwards,

so my root directory/folder will just fill-up 
i can create another folder , but i think it will just be in the (admin) root directory  , so it doesn't make sense (haven't tried yet)


i tried with su,  sudo and just kino    even chown user name /dev/raw1394  ,

but still have the "error modules not loaded and  no permission read write failure " thing going on 


i'm going to try to add the user to the videogroup    (which i tried with normal user, without succes)


what else can i try , root seems to have the privileges now , how can i change this :(

in another forum there was something like rmmod eth1394 or rmmod ieee1394 , which is to remove the module , why i don't know , but it just gave me errors nothing else

---

### Post by firedancer on 2007-08-27
:popcorn:

---

