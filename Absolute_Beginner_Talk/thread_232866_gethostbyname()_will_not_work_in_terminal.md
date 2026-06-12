---
title: "gethostbyname() will not work in terminal"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by chopper81 on 2006-08-09
This is only one of my systems problems at this time. It all started with that >>>>> network. Any help would be great.
chopper81

---

### Post by dusu on 2006-08-09
what's the exact problem ?

---

### Post by chopper81 on 2006-08-09
I was trying to ste up the wireless network on my system last night and I removed the hostname. NOT GOOD I SEE NOW. ANy way I was reading another post and I tried to <ctrl> <ALT> <f1>, type in sudo pico /etc/hostname, but it still says that it is unable to lookup via gethostbyname().
chopper81

---

### Post by dusu on 2006-08-09
Is gethostbyname available on your machine ? I mean : is the packet providing this program installed ?

---

### Post by chopper81 on 2006-08-09
I had never tried to use it before now, but I do know that I had never seen this error until I removed the host name. Is there a place that I can look to see if it is in the package?
chopper81

---

### Post by bscbrit on 2006-08-09
Seriously, have you tried a reboot since you changed the name?  If you haven't, the system is still set to the old name (hence it cannot look it up).  But the new name will only be adopted when you reboot.  The clue is to look at the command line. If it still says user@oldname then the system has not completed the change.

---

### Post by chopper81 on 2006-08-09
I have tried to reboot many times since last night. All I have in the command line is <user>@:~$. Any ideas?
chopper81

---

### Post by dusu on 2006-08-09
First try to type
```
which gethostbyname
```
and see if there is a path to the program (if you have no answer, then it's not installed)

if not, try :
```
apt-file search gethostbyname
```
and look what package provides it.

Note that you may have to install apt-file first :
```
sudo apt-get install apt-file
sudo apt-file update
```

---

### Post by chopper81 on 2006-08-09
I tried everything that you just said and  all I got was two <commands not found> and one <unable to lookup via gethostbyname()>

---

### Post by bscbrit on 2006-08-09
I think (but could be wrong) that you only deleted the previous name but have not provided a newname.  You should see user@hostname:~ The fact that yours shows no hostname would explain why it cannot look it up.

I'm not sure how you changed the hostname in the first place but, if you can get back there, then set it back to the original. (That will give you the most chance of recovering the system).  If you cannot get back, edit /etc/hostname to the oldname again, and edit /etc/hosts to reflect it also.  A controlled reboot should get you back up and running.

---

### Post by chopper81 on 2006-08-09
Thank you for your time I will try this and see what happens. By the way I was trying to change the name of the hostname to something else and did ot realize that I left it empty until I saved it that way. Could you tell me what the host name is for. Does it matter what it is if I want to use different networks? Thank yiu again,
Chopper81

---

### Post by bscbrit on 2006-08-09
The hostname is the name by which the computer knows itself, or by which it is called on a network.  It is the former function that is causing you a problem because it uses its own hostname to carry out various essential tasks.  In your case, it probably hasn't got a valid hostname and therefore cannot carry out those tasks - hence the error messages.  The hostname is also the name by which other computers on the same network will refer to it.  This purpose is only relevant if you are on a network.

---

