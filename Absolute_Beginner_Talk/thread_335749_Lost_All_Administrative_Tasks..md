---
title: "Lost All Administrative Tasks."
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by tickmike on 2007-01-10
Hello All.

This is a great site thankyou all who help out.

Ok my next problem I decided to change my computer name.
System>administration>networking>general tab change name.click ok. reboot.
 Did that ok .

Now I have lost all my administrative tasks Eg Terminal , any things under System>administration do not work.
I have an 1 update, that does not work.

Any get around please.


Michael

---

### Post by ComplexNumber on 2007-01-10
you need to add/change the new name to the admin group. go to main menu -> system -> administration -> users and groups. click on 'manage groups', look for admin and highlight it. then select 'properties. this doesn't need admin rights.

btw how exactly did you change your username?

---

### Post by taurus on 2007-01-10
You need to boot your machine into recovery mode from GRUB menu and have a look at your /etc/hostname & /etc/hosts.  Make sure they both have the same name.  If not, change them.

```
nano /etc/hostname
nano /etc/hosts
```
Then, reboot with

```
shutdown -r now
```

---

### Post by tickmike on 2007-01-11
Thanks 
a-bi  ...you said ... **btw how exactly did you change your username?**
That's in my first post !... System>administration>networking>general tab change name.click ok. reboot.

taurus...you said....**You need to boot your machine into recovery mode from GRUB menu**
Is that where you put your Edgy Eft   CD in and run recovery and it ends in a 'prompt' command and then I can copy/paste your script in ?.

Regards Michael.

---

### Post by jvc26 on 2007-01-11
taurus means when you boot your PC and it goes into GRUB (i.e. the bootloader for linux) open the menu for GRUB (ESC key when you load) then select 'recovery mode' from the boot options.
Il

---

### Post by taurus on 2007-01-11
No.  When you turn on your computer (without the LiveCD), you will have three seconds to press something when you see the GRUB on the screen.  Press Esc to see the menu and pick the Recovery mode to boot it up.  Otherwise, you can boot with the LiveCD, mount your harddrive where / is, and edit those two files on the harddrive.

---

### Post by tickmike on 2007-01-11
Thanks ..I will try later..

---

### Post by tickmike on 2007-01-11
I booted up as above.

I tried putting   "nano /etc/hostname"   then pressed enter , then I got a screen with GUN nano 1.3.10 etc.along the top of screen.and it told me my new host name. 

But then I could not get out of that screen.   I had to switch the computer off.

I then did the same with  "nano /etc/hosts"    then I got the above screen up with my new computer name and underneath it the old one ( yes they are different). no other commands would work in that screen. switched off again.
 Could not see how to get to the /  with the live cd    

Michael.

---

### Post by taurus on 2007-01-11
To exit nano, hold down <Ctrl> while pressing x.  Then answer the questions with **Y** to save it and return.  ^X at the bottom means <Ctrl>x.

---

### Post by tickmike on 2007-01-11
Thanks ..I tried to use ^ key ( above 6 ) and x  key.....opp's  . 
You will have to remember I'm still on the steep part of my learning curve !!! .

Made changes and answered  'y' to save .

now its asking for ...

File name to Write /etc/hostes        ?

Michael.

---

### Post by taurus on 2007-01-11
When it asks you to save it to /etc/hosts, just hit the return because you want to save the change to /etc/hosts.

---

### Post by tickmike on 2007-01-12
I did exactly what you said checked and rechecked but it still does not work, (did a reboot ) try using 'Terminal' and it keeps saying "Sudo  unable to look up via gethostbyname" also updater will not work or any administration tasks.

What do I try now please.

---

### Post by ComplexNumber on 2007-01-12
> **tickmike said:**
> I did exactly what you said checked and rechecked but it still does not work, (did a reboot ) try using 'Terminal' and it keeps saying "Sudo  unable to look up via gethostbyname" also updater will not work or any administration tasks.

What do I try now please.
try my original suggestion.

---

### Post by tickmike on 2007-01-12
> **ComplexNumber said:**
> try my original suggestion.

Hi , I did and as I said no administration tasks work, so it failed.

---

### Post by ComplexNumber on 2007-01-12
> **tickmike said:**
> Hi , I did and as I said no administration tasks work, so it failed.
oh, i see. mine doesn't ask for a password, although i would have thought it required it.

---

### Post by tickmike on 2007-01-12
> **ComplexNumber said:**
> oh, i see. mine doesn't ask for a password, although i would have thought it required it.
  

I have two test computers running side by side and the good one needs your password for what you suggest .

But this is to change the user name !!!...I have changed the Computer Name. !!!

---

### Post by ComplexNumber on 2007-01-12
> **tickmike said:**
> I have two test computers running side by side and the good one needs your password for what you suggest .

But this is to change the user name !!!...I have changed the Computer Name. !!!
thats why i was confused :D. i really must put my specs on because i have been reading "username" where you've said "computer name". d'oh! i was wondering why taurus was suggesting that particular plan of action

---

### Post by tickmike on 2007-01-14
Now what do I do ?. ( see my 1st post on other page.)

Does any body have any ideas what I can try now to solve my problem OR should I put a new post in one of the other parts of the forum ?.

From Michael.

---

### Post by taurus on 2007-01-14
Post these three commands (outputs) here!

```
id
cat /etc/hostname
cat /etc/hosts
```

---

### Post by tickmike on 2007-01-14
Hi taurus,  As you can see I did this in a Terminal .  e vectra is my new computer name, my old computer name was Desktop . BUT this was confusing me when I was using Terminal etc.

michael@e vectra:~$ id
uid=1000(michael) gid=1000(michael) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(michael)
michael@e vectra:~$ cat /etc/hostname
e vectra
michael@e vectra:~$ cat /etc/hosts
127.0.0.1 localhost e vectra
127.0.1.1 e vectra

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
michael@e vectra:~$

-------------------------------------------------------------------------------------------------

---

### Post by taurus on 2007-01-14
I would remove the "e" from /etc/hostname and make /etc/hosts to look like this.

```

127.0.0.1 localhost
127.0.1.1 vectra

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
michael@e vectra:~$

```

And of course, you have to do all that from the recovery mode.

---

### Post by tickmike on 2007-01-14
Hi taurus.

You have solved yet another problem, well done go to the top of the class. :D 

So what happened why did having 'e' make all the difference, is it a command.?.

You probably know that e vectra is a sff HP computer and being I am testing Two ubuntu machines side by side I decided to use the computer makers names for my computer names.

Is it not the correct way to change the computer name ...System>administration>networking>general tab change name.click ok. reboot.
Michael

---

### Post by taurus on 2007-01-14
> **tickmike said:**
> Hi taurus.

You have solved yet another problem, well done go to the top of the class. :D 

So what happened why did having 'e' make all the difference, is it a command.?.

You probably know that e vectra is a sff HP computer and being I am testing Two ubuntu machines side by side I decided to use the computer makers names for my computer names.

Is it not the correct way to change the computer name ...System>administration>networking>general tab change name.click ok. reboot.
Michael

I think the system thought "e" is one name and then "vectra" is another.  I don't think you can use multiple names for one machine at the same time.  If you want to call that machine by the manufacturer's name, then you can use the "e_vectra" if you wish.

p.s.  Rather stay behing the line then...

---

