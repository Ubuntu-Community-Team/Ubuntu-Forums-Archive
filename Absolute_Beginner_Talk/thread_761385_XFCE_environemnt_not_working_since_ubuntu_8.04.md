---
title: "XFCE environemnt not working since ubuntu 8.04"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by rajaram_s on 2008-04-21
I just upgraded my laptop from ubuntu 7.10 to ubuntu 8.04. The XFCE environment was working great until I made the upgrade. Since the upgrade, whenever I select the XFCE session, a blank screen comes, and I just have to reboot the system, there is no other choice... is this a bug in hardy heron or should I make any changes?

---

### Post by LowSky on 2008-04-21
Hardy is still a BETA, things dont always work.

try reinstallliung the XFCE, see if that ork, maybe a file became corrupted.

---

### Post by What is in a name? on 2008-04-24
Also happened in my PC. Today Hardy went final and this problem is still there. I already purged and installed Xfce again several times in my machine. I renamed my Xfce and Xfce-session definitions folders in my Home directory with a _bak in the end so that the system could start a fresh session of Xfce... And nothing. I can only boot once, and after I logout I can't login again no more.

---

### Post by sports fan Matt on 2008-04-24
My Xfce works great in Hardy..I had to purge it a few times too to get all the configurations straight..

---

### Post by rajaram_s on 2008-04-25
k... I'll wait for the updates of hardy heron then.... I tried reinstalling XFCE too... it dint work!

---

### Post by ophion on 2008-04-29
I am running the release version (64-bit Ubuntu base), and Xfce sessions fail in the way mentioned above.  This is an incredibly shaky release (LTS, no less!).  Having a beta browser as default is certainly a glaring error (I cannot access my bank with the default browser?  Utter failure.), but having variants that seem to have not been tested at all is a deeply disturbing sign.  Is this ship sinking?  From the evidence at hand, 8.04 truly appears to render Microsoft's Vista release a triumph of project management.

---

### Post by Mazza558 on 2008-04-29
Yeah, I have the same problem now.

---

### Post by Ctroncoa on 2008-05-02
Try deleting libpam-gnome-keyring , that's how I got XFCE to work with Ubuntu 8.04. Hope this helps.

---

### Post by kamonn on 2008-05-03
This is totally annoying. Just happened to me on a fresh install. Logged into Xfce, enabled compiz, logged out and when trying to login in Xfce just won't start anymore. At first I thought it was some sort of compiz related bug, then I read this thread. 
> **Ctroncoa said:**
> Try deleting libpam-gnome-keyring , that's how I got XFCE to work with Ubuntu 8.04. Hope this helps.
Didn't work for me :/

---

### Post by aschrempf on 2008-05-09
I had the same problem - xfce was not starting correctly on Hardy (Ubuntu 8.04), was hanging on blank screen with only the mouse pointer working.

It was funny that the following was reproducable - killing X (Ctrl-Alt-Backspace) 2 times and logging in again - xfce was starting. However it is not funny that 3 logins are required in order to start xfce.

So I tried to find out a bit more. Observing the .xsession-errors file in the home-dir I found that in the case where xfce was not starting I had 

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 47 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 48 overrides entry on line 7
Agent pid 15222

and nothing more - hence the whole thing hangs on the agent with pid 15222. Hence when ps -ef |grep 15222  it turns out that the agent is /usr/bin/ssh-agent. And it seems that the program hangs - on which reason however.

So i did the following:

1) copy /etc/xdg/xfce4/xinitrc to ~/.config/xfce4/xinitrc
2) edit ~/.config/xfce4/xinitrc and comment out any line which has to do with the sshagent:

line 65:
# Use ssh-agent if installed and not already running.  Run it separately
# so it populates the environment here, so we can clean it up later.
#sshagent=`which ssh-agent`
#kill_sshagent=0
#if test -z "$SSH_AGENT_PID" -a "$sshagent" -a "x$sshagent" != "xno"; then
#	eval `$sshagent -s`
#	kill_sshagent=1
#fi

line 90:
#		if test $kill_sshagent -eq 1; then
#			eval `$sshagent -k`
#		fi

line 179:
#if test $kill_sshagent -eq 1; then
#	eval `$sshagent -k`
#fi

3) and now it seems, that the problem was solved. What the ssh-agent is responsible for I am not sure, but for me there seems no restriction without this agent


I hope this will be useful for you,

Best regards, Andreas

---

### Post by smithji2005 on 2008-05-12
Thanks this seems to be working for me.

---

### Post by rajaram_s on 2008-06-01
I even tries  reinstalling XFCE, it dint work for me...

---

### Post by djluvsgod on 2008-06-04
ssh is for secure connections between computers, I'm not sure how disabling this will affect your ability to connect to websites securely (like your bank account)

I read another thread where someone was having problems using their ssh, it turns out, that it was being rejected in some cases because of the security patch update to do with the random number generator. I don't know if you heard of it, but it was a major flaw that came from debian, the random number generator was faulty. Even on a fresh install of Hardy I have this problem, so if it is indeed something to do with the number generator, I assume it's because something was changed as to location or operation with the patch...

Just a guess.

I really want my xfce back.....;P

---

