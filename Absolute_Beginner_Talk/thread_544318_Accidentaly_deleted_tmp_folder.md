---
title: "Accidentaly deleted /tmp folder"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by cytutchi on 2007-09-06
i deleted the /tmp folder

but from a friend i copied back the .X11-unix and the .X0lock file
but still i cant login to my kubuntu
i give us/pass n then...a bit of black screen n back to login page

P.S. the space on my hard disk is ok (50% free)

What can i do?? :(((

---

### Post by steve.horsley on 2007-09-06
I think yoy should be able to press Ctrl-Alt-F2 and get a b&w login screen. Log in and enter this command:
**sudo chmod 1777 /tmp**
Hopefully that will do the trick. 
P.S. All it is doing is setting the directry permissions to the right value.

---

### Post by cytutchi on 2007-09-06
> **steve.horsley said:**
> I think yoy should be able to press Ctrl-Alt-F2 and get a b&w login screen. 

Can i do this by login in with safe mode? the one that is only konsole and no visual grpagics or Ctrl-Alt-F2 is the same thing?

> **steve.horsley said:**
> **sudo chmod 1777 /tmp**

shouldn't i use the chmod -R command to be recursive to change everything inside or that will be enough?
Also 1777 is different from 777?

Thank you for trying to help n sorry if i ask more...just want to understand!

P.S. what about the files inside the /tmp folder that i am missing? like X0 in side of .X1-unix....should i do something about that?

---

### Post by cytutchi on 2007-09-06
YESYEYSYESYEYSYESYEYOSIERUOWIEUROIWUEROWUOERAOSFJNASNFLKN
:)))))))))))))))))

sorry for the above but it's laughs n screams of happiness!!!

ve'been trying to make it work for 2 days now and finally that was the problem! The permissions rights on the /tmp folder!!!

How did you know that?

I guess it's because i deleted it n then recreated it as root it took permission only as root or smthing??? Really great though n thank you again so much! :)

Bythe way...still i would like to know if it helped that i copied the contents of the /tmp folder from a friend of mine or even if i hadnt done it, created a tmp n changed permissions would be enough!?

Thank you steve again and thank you community!

---

### Post by dwhitney67 on 2007-09-06
> Bythe way...still i would like to know if it helped that i copied the contents of the /tmp folder from a friend of mine or even if i hadnt done it, created a tmp n changed permissions would be enough!?
I do not see the relevance of copying the contents of anything to the /tmp folder from one system to another.  Generally when the system starts up the /tmp folder is a clean slate.  When certain applications are launched, they may insert "lock" files or other data files in /tmp as a temporary repository for such.

If you should delete the folder again (one must wonder why you did it in the first place!), just follow the instructions given previously:
[FONT="Courier New"]
$ sudo mkdir /tmp
$ sudo chmod 1777 /tmp[/FONT]

Then I would recommend a reboot:
[FONT="Courier New"]
$ sudo shutdown -t0 -r now[/FONT]


P.S
I would also recommend that you redefine the "rm" (remove) command for each account on your system that has sudo or root privileges.  Add the following to each account holder's *~/.bashrc* file or add it to the */etc/bash.bashrc* file:

[FONT="Courier New"]alias rm='\rm -i'[/FONT]


P.S.S.
If you are satisfied with the responses in this thread and your problem is solved, pull-down the **Thread Tools** and designate this thread as being closed.

---

### Post by steve.horsley on 2007-09-06
Looks like I made somebody's day. That's always rewarding. Glad to be able to help.

> How did you know that?
It was a guess. I couldn't think of anything else that might be the problem, assuming you had recreated the /tmp directory with the right name. And if you made the wrong name, that command would have given an error message. The contents of /tmp are not important - it's not unusual to delete the contents of /tmp upon reboot. So copying the contents back from another PC was probably wasted effort.

I agree with dwhitney67 that **alias rm='\rm -i'** in /root/.bashrc is a good idea.

---

