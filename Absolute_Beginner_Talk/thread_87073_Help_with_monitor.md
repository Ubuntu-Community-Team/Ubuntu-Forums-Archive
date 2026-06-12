---
title: "Help with monitor"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by Brad.G on 2005-11-07
ok heres the run down. never touched a linux pc until this morning..

had a problem with the resolution of the monitor and found a post on here about typing 

sudo gedit /etc/X11/xorg.conf

there wasnt  the 
HorizSync 30-70
VertRefresh 50-140
lines so i added them , saved the file, rebooted the server.... and the monitor isnt switching on? lol HELP

you get the black screen as its loading with all the 
ok
ok
ok
ok
ok
 down the right hand side.. then the light on the onitor goes orange and thats it.. any ideas?

the good news is the servers up.. everyone can access files and so on ... just now i cant see anything on it :o|

---

### Post by Brad.G on 2005-11-07
hey heyyyyyy

i fixed it :) 

ok it may sound sad to you but im chuffed! lol

turned out the monitor didnt like the changes... i put a different monitor on it and it works fine , with lots of different resolutions now available.

which brings me to my next question...

im not sure what version of linux was on this before they put ubuntu on it..

but i can remember watching the IT Tech using webmin to configure the user names and passwords and whaty group they belong to..

well this is what i need to do now, change users passwords, and security levels as half of our staff cant get on the server which is no good.

where do i go to do this?

i went to

system>administration>users and groups

but i dont think this is what i should be altering, as isnt this just for logging on to the server as a user? not accessing the files on it over a Lan?

i dunno ... like i said, first time ive used this before

feels like im standing in the middle of a BIG empty field holding a HUGE sign which reads "Totally clueless!"

---

### Post by Original Brownster on 2005-11-07
Hi,
How do you want users to be able to connect to the server to download files - do you mean via a mapped network drive or perhaps via a web browser. Are users using windows clients or are they on linux / unix as well?

I'll assume they want to map network drives in which case you need (System > Administration > shared folders ) and then for users using windows clients configure samba or for linux users configure NFS.

This is a pointer in the right direction, you'll probably need to have a look at the docs for samba because you can configure the security in many ways depending on your lan setup.

HTH

---

