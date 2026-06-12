---
title: "Error on bootup (install apt ?_)"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Likenota on 2007-08-19
yea for some reason after i updated i get this error message when i boot up and it tells me to install apt ? how do i go about that...  get-apt install apt ?....

---

### Post by Jimmyfj on 2007-08-19
Could you post the message here? this makes it a lot easier to help out

---

### Post by Likenota on 2007-08-19
okay when i boot it gives an error of something being in the file system error so it runs the check then a bunch of numbers display then it says check failed...

Automatic file system check failed  the root file system is mounted in read only mode..





it also says:

  the program 'apt-get' is currently not installed you can install it by typing apt-get install apt  



and that doesnt work either... so how do i change it to read and write? and how on earth am i suppose to isntall apt when it didnt even work for the command, i have compiz fusion and vmware so i dont understand how i dont have the apt thingy. please help.

---

### Post by Boreras on 2007-08-19
done anything weird before getting this error? Always had this error with this install? How do you use "apt-get install apt" anyways without proper booting? LiveCD?

If you could paste the line from fstab about your root partition, that would be helpful too.

---

### Post by Likenota on 2007-08-19
no nothing wierd before this, and also this never happened before.. hmmm how do i paste the partition info... etc etc how do i bring info on that up.. also can i use live cd to do maintaince or auctually read the file system partition? perhaps there is a way to get it to work with that...

---

### Post by ChocoLATE on 2007-08-19
I am having the same issue and it just started when I rebooted.

---

### Post by Likenota on 2007-08-20
any ideas anyone ? it seems that this is an issue that can be fixed, but if several people are having the issue it should be answered!

---

### Post by ChocoLATE on 2007-08-20
I agree...I was fine until I rebooted due to my microphone on my laptop not working in skype.  Typically if I restart my system it clears up and instead I became stuck. :confused:

---

### Post by fishwater on 2007-08-21
I am having this problem as well. Happened after I rebooted

---

### Post by mitanc on 2007-08-21
I also had this problem.  It told me to hit CTRL-D to exit, I did and normal boot up continued.  I think it was related to the fact that the HD checking failed and it exit out of the boot.  Lastly, my HD are IDE, but they are being detected by Ubuntu as SCSI, they are called sca1 and scb1.  

When I have my USB drive inserted the drives name becomes scrambled as well.  Any solutions?

---

### Post by Likenota on 2007-08-25
umm okay this is really fun i cant even boot in linux and still no solutions? please please help us out here.

---

### Post by cjking on 2007-08-26
Having the same problem turned it off one night,started it up the next morning and fs is read only.  I tried everything I know of.  Using 7.07 Server.  I can mount the file system manually,  But all of my servers and wireless card must also be started manually.  I've scanned the fs and it comes back clean at times and than other times comes back with journal repaired.  Really strange.   I can't boot from the installation cd because the OLD laptop I have it installed on has no cd or floppy drive (old LifeBook).

None of my other systems have this problem.  I have 7.07 Server installed on a Dell server and it is nearly identical to the LifeBook minus the fs problem of course. Desktop and other laptop are running fine.

I only use the LifeBook for testing so it isn't a major problem for me.  I just hate having something going on that I don't understand.  if anyone finds the root of the problem and a solution please post it here.

---

### Post by Likenota on 2007-08-27
bump* okay seriously this is suppose to be a help forums is there anyway anyone can help out?! or are you guys all gonna just sit there and not even tempt to help.

---

### Post by mrphd on 2007-08-28
I have experienced a similar error, and it was also complaining about a problem with the file system. If this is the case with you, try:

```
fsck -v
```

and fix any errors with the file system. After it finishes (it will tell you when) restart and see if this helps.

I've now had this error twice this month, and I still can't work out the cause of it...

---

### Post by Likenota on 2007-08-28
thanks much this worked. :)

---

### Post by Sunflower1970 on 2007-09-29
As of this morning, this happened to me on my laptop. It's my /home partition that has the errors on it, supposedly. It happened after the update to kernel 2.6.20-16-generic that I had been avoiding (since I use the Gutsy kernel on it for one, and secondly, when I updated the -16 generic kernel on my desktop it borked it up and I had to reintall everything.) Not too sure what to do now....fsck -v  I'm doing that now...it took a very long time, but that seemed to fix it....*crosses fingers it'll stay fixed now...*

---

