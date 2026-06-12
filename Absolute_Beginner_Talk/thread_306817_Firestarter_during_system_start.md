---
title: "Firestarter during system start"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by henrywm on 2006-11-25
I set Firestarter to load when the system boot by adding "gksu firestarter" to the "Startup Programs" tab of the Sessions dialog. Now I have two problems:
1) I need to type my password when I log in and then type it again when Firestarter loads. Can I fix this?
2) The Firestarter window is open when the login is complete. Can I configure it to run with the window closed by default?

---

### Post by 5-HT on 2006-11-25
> **henrywm said:**
> I set Firestarter to load when the system boot by adding "gksu firestarter" to the "Startup Programs" tab of the Sessions dialog. Now I have two problems:
1) I need to type my password when I log in and then type it again when Firestarter loads. Can I fix this? 

You could edit your *sudoers *file -- using *visudo --* to allow Firestarter to run without a password. There are lots of threads around describing how to do so (the *man *page for *sudo* describes everything in detail as well).
> **henrywm said:**
> 
2) The Firestarter window is open when the login is complete. Can I configure it to run with the window closed by default?

Yes. Just add **--start-hidden **to the startup command in the sessions dialogue.

HTH

---

### Post by henrywm on 2006-11-25
> **5-HT said:**
> 
Yes. Just add **--start-hidden **to the startup command in the sessions dialogue.

HTH

This worked, but it removed the icon from the panel at the top. Can I do this but still keep it in the panel?

I will need to research the other issue later when I have some time.

---

### Post by henrywm on 2006-11-25
> **5-HT said:**
> You could edit your *sudoers *file -- using *visudo --* to allow Firestarter to run without a password. There are lots of threads around describing how to do so (the *man *page for *sudo* describes everything in detail as well).

HTH


Can you elaborate more? I am very new to Linux.

---

### Post by 5-HT on 2006-11-25
> **henrywm said:**
> Can you elaborate more? I am very new to Linux.

Sure. To get Firestarter to run without a password:

1. In a terminal (applications -> accessories -> terminal) type
```
 sudo visudo 
``` to open the sudoers file for editing.

2. add the following line (replacing **username **with your own username)
```
 **username **ALL= (root) NOPASSWD: /usr/sbin/firestarter 
```The Firestarter GUI will now be able to run without a password.

Note that it should not be necessary to start Firestarter's GUI in order to have a functioning firewall-- it's running behind the scenes.
 Starting with Dapper, however, there may be a possible bug ([https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647](https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647))  in which the firewall does not start automagically as it should. In that case, having the GUI start automatically ensures the firewall does so as well.

If you're still having problems getting the GUI to start on boot, the following little hack may be required:[http://ubuntuforums.org/showpost.php?p=1599809&postcount=3](http://ubuntuforums.org/showpost.php?p=1599809&postcount=3)

With regard to the panel icon not being present when calling Firestarter with 'start-hidden', the issue is likely due to either 1)not having Firestarter set up to start without a password, or 2) Firestarter's GUI simply isn't loading on boot as you'd like. Hopefully this post will address 1) and the link above 2).


Hope that helps. Post back if you're still having problems.

---

### Post by henrywm on 2006-11-27
Now I cannot load the GUI at all (at startup or manually)

---

### Post by henrywm on 2006-11-28
I followed the "sudo visudo" isntructions above. Now I cannot load the firestarter gui at all. Do you have any suggestions?

---

### Post by 5-HT on 2006-11-28
> **henrywm said:**
> I followed the "sudo visudo" isntructions above. Now I cannot load the firestarter gui at all. Do you have any suggestions?

Did you perform the following? It applies to calling the application manually as well as for an autostart.
[quote=5-HT]
If you're still having problems getting the GUI to start on boot, the following little hack may be required: [http://ubuntuforums.org/showpost.php?p=1599809&postcount=3](http://ubuntuforums.org/showpost.php?p=1599809&postcount=3) [/quote]

---

### Post by DannyG on 2006-11-29
If you installed FireStarter from binary, it automatically loads at startup, even although you don't get the icon.

To check to see if FireStarter is running:

```
sudo /etc/firestarter/firestart.sh status
```

Then you can start and stop FireStarter by replacing "status" with "start" or "stop" etc.

You don't need to start editing startup files...

---

### Post by henrywm on 2006-11-30
> **DannyG said:**
> If you installed FireStarter from binary, it automatically loads at startup, even although you don't get the icon.

To check to see if FireStarter is running:

```
sudo /etc/firestarter/firestart.sh status
```

Then you can start and stop FireStarter by replacing "status" with "start" or "stop" etc.

You don't need to start editing startup files...


The directory has a firestarter.sh but it will not execute. The computer says "command not found."

---

### Post by henrywm on 2006-11-30
> **5-HT said:**
> Did you perform the following? It applies to calling the application manually as well as for an autostart.

Yes. It did not load firestarter.

---

### Post by 5-HT on 2006-11-30
> **henrywm said:**
> Yes. It did not load firestarter.

That script has worked on Dapper and Edgy, curious why you're still having problems.

If you enter the following in a terminal does Firestarter's GUI start? If not, what error are you getting?
```

xhost +local: && sudo firestarter --display :0.0 
```

---

### Post by henrywm on 2006-11-30
> **5-HT said:**
> That script has worked on Dapper and Edgy, curious why you're still having problems.

If you enter the following in a terminal does Firestarter's GUI start? If not, what error are you getting?
```

xhost +local: && sudo firestarter --display :0.0 
```

It says "non-network local connections being added to access control list" and asks for my password. It loads the GUI after I enter my password. It does not ask for my password to load firestarter during boot up.  Instead it does not load firestarter.

---

### Post by henrywm on 2006-12-08
Does anyone have suggestions on how to fix this?

---

### Post by Paul41 on 2006-12-08
> The directory has a firestarter.sh but it will not execute. The computer says "command not found."

There was a typo in the file path posted. Change firestart.sh to firestarter.sh and it should run.

```
sudo /etc/firestarter/firestarter.sh status
```

---

### Post by henrywm on 2006-12-09
That allows me to check the status. Thanks.

My main problem is getting firestarter to load automatically without requiring a password. So far I have been unable to do that. Do you have any advice?

---

### Post by 5-HT on 2006-12-11
> **henrywm said:**
> It says "non-network local connections being added to access control list" and asks for my password. It loads the GUI after I enter my password. It does not ask for my password to load firestarter during boot up.  Instead it does not load firestarter.

Sorry for the delay. Looks like you are being prompted for a password when calling Firestarter because there may be an issue with your sudoers file. If so, this would also explain why there are still problems on autostart. 
Do you have line similar to this at the end of /etc/sudoers?

your_username_here ALL= (root) NOPASSWD: /usr/sbin/firestarter

Additionally, you will need to add the script (the one I linked to earlier calling Firestarter and containing xhost +local: ) to your startup list-- instead of Firestarter's executable.
Someone mentioned earlier that this was not needed on Edgy though others are still having problems.

---

### Post by vgrisham on 2006-12-24
> **5-HT said:**
> Sure. To get Firestarter to run without a password:

1. In a terminal (applications -> accessories -> terminal) type
```
 sudo visudo 
``` to open the sudoers file for editing.

2. add the following line (replacing **username **with your own username)
```
 **username **ALL= (root) NOPASSWD: /usr/sbin/firestarter 
```The Firestarter GUI will now be able to run without a password.

Note that it should not be necessary to start Firestarter's GUI in order to have a functioning firewall-- it's running behind the scenes.
 Starting with Dapper, however, there may be a possible bug ([https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647](https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647))  in which the firewall does not start automagically as it should. In that case, having the GUI start automatically ensures the firewall does so as well.

If you're still having problems getting the GUI to start on boot, the following little hack may be required:[http://ubuntuforums.org/showpost.php?p=1599809&postcount=3](http://ubuntuforums.org/showpost.php?p=1599809&postcount=3)

With regard to the panel icon not being present when calling Firestarter with 'start-hidden', the issue is likely due to either 1)not having Firestarter set up to start without a password, or 2) Firestarter's GUI simply isn't loading on boot as you'd like. Hopefully this post will address 1) and the link above 2).


Hope that helps. Post back if you're still having problems.

How do I save the changes I make in visudo? :confused:

---

### Post by 5-HT on 2006-12-24
> **vgrisham said:**
> How do I save the changes I make in visudo? :confused:

Depends on which editor you're using. The default would be nano, and in that case: ^x (control + x) to exit, and 'y' to save changes.
HTH

---

### Post by morphh on 2006-12-26
I am having similar problems.  When I check the status, it says it is running but I do not get a icon in the tray and when I try to launch it manually.. it runs for a sec and disappears.  I've tried to put both the bash script and the --start-hidden in the startup session.  Just can't seem to get the icon.  Sodoers seems to be working fine as I can launch the script without entering a password.

---

### Post by Floppyjoe on 2006-12-28
I also have a similar problem using Ubuntu 6.10. I've done all the steps listed in this thread. When my computer boots up firestarter is running in the background but the gui is not visible. The start up script does not work to get the gui running.

```
xhost +local: && sudo firestarter --display :0.0
```

This does start the gui without the password from the terminal but that does not help much.

On a positive note this script did work for my laptop and the gui there loads during bootup.

---

### Post by benyau on 2007-01-02
This simple method works for me:
- sudo visudo, add username ALL=(root) NOPASSWD: /etc/init.d/firestarter
- in Sessions/Startup Programs, add sudo /etc/init.d/firestarter restart

---

