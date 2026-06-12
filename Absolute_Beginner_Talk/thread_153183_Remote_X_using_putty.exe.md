---
title: "Remote X using putty.exe"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-03-31
Does anyone have any experience doing this?  I've got x11 forwarding set to yes in the sshd_conf.  But can't get it to work.  I'm connecting using putty.exe on a windows box at work.

---

### Post by jstueve on 2006-03-31
do you have an Xserver on your windows box at work?

---

### Post by echo $USER on 2006-03-31
no, I don't.  Is that the problem?  I'm trying to connect to my machine at home.

---

### Post by stuporglue on 2006-03-31
Yeah, you need an X server on the box you're connecting from. I don't think Putty.exe can do it by itself. You probably need to install Cygwin it has an X server for Windows

---

### Post by xenmax on 2006-03-31
yeah, i think putty by default is only a text terminal.

If you need X, you try Cygwin like suggested above (don;t know if it is free or otherwise). You can also try Exceed by Hummingbird for which i believe you need to  purchase licenses - but gives better performance IMO.

---

### Post by echo $USER on 2006-03-31
Nice, thanks for the replys guys.

---

### Post by nytwolf on 2006-05-10
Are you familiar with Exceed? The company I work at uses it (just recently got it installed on my laptop) and I use it to connect to corporate Linux servers. Though its already all configured for me... I have this file I just double click and it automatically tells Exceed where to go.

I noticed a wizard to help set up new connections to new servers, but it gives me a list of methods (the list is: REXEC, RSH, RLOGIN, TELNET, and PCX$SERVER) and I'm not sure which I should use.

Then further on down in the wizard it asks for an Application and Paramters. Two are available in a drop down list (XTerm, which does: Application: @(XTerm, method=stdappdb) Paramters: -display @d&@; and XClock with does: Application: @(XClock, method=stdappdb) -display @d&@;)

I'm not sure what to use in these fields, if I'm using Putty along side it. Could someone offer assistance? And I know I don't have to use Putty alongside Exceed to access the corporate boxes...

---

### Post by xenmax on 2006-05-11
Well, i dont know much at all about setting up Exceed, all i know is how to use it. From your post i could not figure out whether you wanted help about setting up Exceed or using Exceed to connect to linux machines?

So, i will just post here how i use exceed at work:
1. Login(remote desktop) to windows machine where Exceed is installed. In your case, i guess you dont need this step as Exceed is installed in your laptop itself.

2. Launch Exceed. It will assign you a desktop/display id. Note that down. (Example 1.0)

3. Bring up command prompt on windows. Telnet to required linux machine on the network.

4. Assuming bash is the shell, use command (without quotes) "declare -x DISPLAY=x.x.x.x:Z " where x.x.x.x is IP address of machine running Exceed (in your case, your laptop) and Z is desktop id that Exceed gave you. This will setup DISPLAY variable.

5. Now launch any GUI application from command line. Eg: gnome-terminal or mozilla etc.... and those windows should hopefully appear on you laptop.

Hope this helps.

---

### Post by nytwolf on 2006-05-11
Thank you very much! I'll try that out when I get a chance.

---

