---
title: "Failed to start the X server"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Nepenthesrajah on 2007-04-18
For the past few days I have been trying to install beryl with Ubuntu 6.10 with no successes.  I have been following these instructions [https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy](https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy). 

I did not add the 
> Option       "AddARGBGLXVisuals" "True"
Since I did not believe I am NVidia user.  Could that be the problem?  If so how could I fix it without reinstalling my whole ubuntu?

This is the third time I reinstalled all of Ubuntu from 3 different live CD burned with 3 different programs and after I change the /etc/X11/xorg.conf file each it boots to a black screen but if I press enter it comes to a blue and gray screen with meaningless letter around a text box that says…

```
“Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?

<Yes> <No>”
```

So I click yes

Then it comes up and says 

```
“X Window System Version 7.1.1
Release Date 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.15.7 i686
Current Operating System: Linux jeremiah-desktop 2.6.17-10-generic #2
SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
            Before reporting problems, check http://wiki.x.org to make sure that you have the
            latest version.
Module loader present
Markers: (--) probed, (**) from config file, (= =) default setting, (++) from command    line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.  (= =) Log file: “/var/log/xorg.0.log”, Time: Tue Apr 17 17:32:43 2007 (= =) Using config file: “/etc/X11/xorg.conf”
Parse error on line 151 of section DRI in file /etc/X11/xorg.conf
              “EndSection” in not a valid key word in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatel server error:
No screens found

       <Ok>k>”
```

So I select “Ok” and is asks me…
```
“Would you like to view the detailed X server output as well
        <Yes>S>  <No>o>”
```

Then it says…

```
“X Window System Version 7.1.1
Release Date 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.15.7 i686
Current Operating System: Linux jeremiah-desktop 2.6.17-10-generic #2
SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
            Before reporting problems, check http://wiki.x.org to make sure that you have the
            latest version.
Module loader present
Markers: (--) probed, (**) from config file, (= =) default setting, (++) from command    line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.  (= =) Log file: “/var/log/xorg.0.log”, Time: Tue Apr 17 17:32:43 2007 (= =) Using config file: “/etc/X11/xorg.conf”
Parse error on line 151 of section DRI in file /etc/X11/xorg.conf
              “EndSection” in not a valid key word in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatel server error:
No screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad File Descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad File Descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad File Descriptor

       <Ok>”
```

So I select ok and it says….

```
“The server is not disabled, Restart the GDM when it is configured correctly
             <Ok>”
```

So again I select “Ok”

And it comes up with a black screen that says…

```
“Starting up… Ubuntu 6.10 jeremiah-desktop tty1

Jeremiah-desktop login: _”
```

So I enter my user name and password and it says…
```
"Last login: etc…

jeremiah@jeremiah-desktop:~$”
```


So I have no idea what to enter.  I figured I must have done something wrong so that is why I tried reinstalling from scratch two other times.  

Thanks again for all your help,
-Jeremiah-

---

### Post by dbbolton on 2007-04-18
run ```
sudo dpkg-reconfigure xserver-xorg
``` from the recovery console

---

### Post by Nepenthesrajah on 2007-04-18
Great! But after a few screens I got to 

```
Video cards bus identifier:

PCI: 0:2:0_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
```

I can type in those underlines but I have no idea what to put there.

-Jeremiah-

---

### Post by dbbolton on 2007-04-18
you just hit "enter" through the whole thing

---

### Post by Nepenthesrajah on 2007-04-18
That worked perfect!  Thanks so much!  Now if I can just figure out how to install beryl.

Thanks again,
-Jeremiah-  

PS.  I see that I'm supposed to edit my original post to say the issue was resolved but I don't see that button.

---

### Post by dbbolton on 2007-04-20
> **Nepenthesrajah said:**
> That worked perfect!  Thanks so much!  Now if I can just figure out how to install beryl.

Thanks again,
-Jeremiah-  

PS.  I see that I'm supposed to edit my original post to say the issue was resolved but I don't see that button.
don't worry about it. no one does.

but if you click "edit" then "go advanced", there will be a check box to indicate whether the thread is resolved.

---

