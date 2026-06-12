---
title: "no access to root"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by dashct on 2007-05-21
i had installed ubuntu in my comp and while installation it created the the root name but it never asked for the password...i am not able to access the root terminal.... is there any default pasword for it...??i have access to the normal user account only...please help ...so what should i do now

---

### Post by heimo on 2007-05-21
You should read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wormser on 2007-05-21
The root password is not set up intentually for security.  Use the sudo command and for administrative purposes.  If you have to set root (you shouldn't and don't) then **sudo passwd root**.

---

### Post by mocqueanh on 2007-05-21
Go: System>Administration>User Manager.
You can change root password here.

When login, press Ctrl+Alt+F1 to login *** root

---

### Post by sraak on 2007-05-26
and my first question will be:
what is the installation root default password?

---

### Post by drowner on 2007-05-26
> **sraak said:**
> and my first question will be:
what is the installation root default password?

It is randomly generated.

You don't need it, trust me.

---

### Post by sraak on 2007-05-26
(new laptop keyboard is wierd, sorry this doublepost.

---

### Post by sraak on 2007-05-26
ok, another way of saying this RL situation (i tried to use xubuntu in my laptop, refuses):
i cannot login to X, says (view details in ~/.xsession~errors file):

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default:running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/log/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ubuntu"
/etc/gdm/Xsession: Beginning sesion setup...
/usr/bin/ssh-agent: error while loading shared libraries: /lib/libutil.so.1: invalid ELF header

(total 4 lines.)

basically i am stucked with loginscreen alongside 4 lines of text what i understood like 10 years ago... but linux has grown up, and now i am catching up.

---

### Post by mousejunkie on 2007-05-26
Following message in terminal (whilst trying to use CVS version of cedega):

Running Profile : dx9wine
Enter root Password: 
su: Authentication failure
Sorry.

I had of course entered the regular password from my user account.

Then I used **sudo bash... instead of just bash...**... so I did not need my root password. but now I've got "Please enter CVS password" ...brbrbrl... did anyone notice I'm a noob too

---

### Post by sraak on 2007-05-26
sorry, was i making another too complicated message... i am unfortunately famous of that :-(

the situation again:
i burned xubuntu live-install-CD Feisty Fawn 7.04 ithink, and started my laptop with it.
laptop is: Compaq Notebook 100, AMD K6-2, 475MHz, 192M memory, 4.5G hd.
the result: Xserver started, wants to login as ubuntu user, does that, gives errormessages to file, and the file and errormessages are above.
Question: how to continue booting into Xubuntu itself?

i need to try Xubuntu, because i am sick'n'tired of another OS. i need to be in control of my computer totally, and to use totally, legally free software.

that's it. thank you in advance... ;-)

EDIT:
now i rebooted that machine and it went to xubuntu loginscreen. but, where are the usernames and default passwords for both root and regular user?
what do i type in xubuntu login screen Username: -field?

---

### Post by MST3Kakalina on 2007-05-26
Granted, the last install I did was Dapper, and the error messages you posted I can't make heads nor tails of.

  But IIRC, during installation you were asked to create a username on a REGULAR user level, and password.  Just login with those. If you need to do anything at root level, use sudo and when you're prompted for the password, it's the same password for your regular username.  It's not a special root password or anything.

Hopefully this helped.  But if I am telling you something you already know, I apologize.

Perhaps you can try a different desktop environment, unless you really need to use xfce.


mousejunkie:  are you sure you entered the password correctly?  I know sometimes I type too fast for my own good. :P

---

### Post by sraak on 2007-05-26
"But IIRC, during installation you were asked to create a username on a REGULAR"

nope. nothing. xubuntu cd booted right to the login screen. absolytely nothing before that for humans to interact at all.

---

### Post by rillip on 2007-05-26
> **mousejunkie said:**
> Following message in terminal (whilst trying to use CVS version of cedega):

Running Profile : dx9wine
Enter root Password: 
su: Authentication failure
Sorry.

I had of course entered the regular password from my user account.

Then I used **sudo bash... instead of just bash...**... so I did not need my root password. but now I've got "Please enter CVS password" ...brbrbrl... did anyone notice I'm a noob too

I would contact Cedega support to find out what your CVS password is.  It's already been explained how one can reset the root password above.

sraak: if you can get to a terminal, just look in the /etc/passwd, that's where the usernames are stored.  Then you can run 

sudo passwd $username

where $username is the name you see in passwd.

When you first installed, it should have been from a LiveCD.  It would boot up with out the login screen, just take you straight in to single user mode.  Then during the install process you would have been asked for a username and password.  This is the way Kubuntu and Ubuntu both do it, in any case.  Usually it's right before you get to the driver partitioning section.

---

### Post by sraak on 2007-05-26
ok, i see.

but this one did not ask anything but username... i might have som problems with video, at least some time when i booted i had. also i got some msg about usb hub number whatnot over-current... but now i am downloading alternate cd. i hope that fixes the problem.

if not, i have to ask here again.

---

### Post by mousejunkie on 2007-05-26
> **rillip said:**
> I would contact Cedega support to find out what your CVS password is.  It's already been explained how one can reset the root password above.

sraak: if you can get to a terminal, just look in the /etc/passwd, that's where the usernames are stored.  Then you can run 

sudo passwd $username

where $username is the name you see in passwd.

When you first installed, it should have been from a LiveCD.  It would boot up with out the login screen, just take you straight in to single user mode.  Then during the install process you would have been asked for a username and password.  This is the way Kubuntu and Ubuntu both do it, in any case.  Usually it's right before you get to the driver partitioning section.

The  CVS version is the freely available version of cedega - no support, no warranties... the password thing seemed to be some kind of joke by whoever wrote the script. I later ran into other problems. No matter. After about my n-th attempt to get Linux - Ubuntu in this case, running the way I want(have tried various distros since 199?) and spending several weeks each time trying to get it to do what I thought I could do with it(because others could): Windows Recovery -> fixmbr.

But as I mentioned in another post. I'll get my next PC only with hardware that's on Linux compatibilty lists. - Sorry for going off topic

---

