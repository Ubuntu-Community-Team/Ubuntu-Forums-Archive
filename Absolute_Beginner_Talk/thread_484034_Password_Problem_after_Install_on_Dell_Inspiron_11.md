---
title: "Password Problem after Install on Dell Inspiron 1100"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Christian&gt;&lt;&gt; on 2007-06-25
Hello!  I am totally new to Linux.  Been researching for some time and finally decided to take the plunge. =D>

I have a Dell Inspiron 1100, which has the display problem I've seen on here.  When I did the install from the Live CD, I couldn't see everything on each of the screens asking for info, so perhaps I missed something...

Anyway, I entered my name and a password.  Then it did the install with no errors.  After rebooting it is asking for my name and password but it says that I have it wrong!  WHAT CAN I DO?](*,)

---

### Post by BobCFC on 2007-06-25
Both the the name and password are cAse SeNSitve?

---

### Post by Christian&gt;&lt;&gt; on 2007-06-25
I appreciate that...  I typed it in exactly as I did when I installed.  The password is all numbers actually.  

Someone told me to try and get to the "lilo" prompt during bootup, but I don't know how to do that...  I don't see any such options during the startup.

---

### Post by bodhi.zazen on 2007-06-25
Boot to the recovery mode ...

At the command line enter : ```
passwd <username>
```

Obviously change <username> to your log in name ;)

If you forgot that , enter less /etc/shadow and you will get a list of users. (You can scroll up and down with the arrow keys ; type "q" to exit less)

This will set a new password.

Reboot ...

---

### Post by derby007 on 2007-06-25
I'm writing this reply from memory so I could be wrong : 

Try this: go into the SAFE mode/option when the grub menu comes up, (if it doesnt ask you for a password!!, note: i'm not using Linux at the moment, so I cant remember if it lets u in without a password!)  then open a terminal window, ie. command prompt, then type : **sudo passwd** *'your username' *   and change it.... otherwise I'm thinking u might be able to do the same command by using/booting a live CD, if u can see the Linux partition in question.

darn: too late......

---

### Post by Christian&gt;&lt;&gt; on 2007-06-25
Thanks that worked.  The username was incorrect.  So I used the shadow list and sure enough, it was my name, but the first letter was NOT capitolized...  Not sure how that happened.  I know I cap'd it when I did the setup.  

Anyway, thanks.  Now I just need to tackle the resolution problem and then get my D-Link DWL-G650 to work. :grin:

---

### Post by ogroef on 2007-07-30
Hi Christian

I am having the same issue as you had.  How do you boot in recovery mode?

regards

---

### Post by bodhi.zazen on 2007-07-30
> **ogroef said:**
> Hi Christian

I am having the same issue as you had.  How do you boot in recovery mode?

regards

It is an option on the grub boot menu ...

---

### Post by ogroef on 2007-07-31
thx :)

---

### Post by ogroef on 2007-07-31
Hi

The grub boot menu is this the function button that you have to press in the main menu

If not how do I get to the grub menu?

Also when I boot from my Hard drive I don't see a menu!

Regards

---

