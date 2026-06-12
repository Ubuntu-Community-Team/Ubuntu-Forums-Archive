---
title: "Dial up issue"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by unelemented on 2007-11-06
I just upgraded from 6.06 to 7.10
and im having issues connecting to the web with dial up
my modem (which is external) dials and appears to connect with its diagnostic lights but when I go into fire fox I get nothing 
The network manager says it has sent and received a few KB but thats about it 

Its a real pain because I have to restart my machine in windows if I want to use the net

---

### Post by Bartender on 2007-11-06
unelemented -
How did you set up the modem?

[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

---

### Post by unelemented on 2007-11-06
Thanks Bar tender
after I installed gnome ppp I dialed and I got this error

WvDial Modem<*1>: User Access Verification
WvDial Modem<*1>: Username: 
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: Username: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: daniel.b
WvDial Modem<*1>: daniel.b
WvDial Modem<*1>: Password: 
WvDial<*1>: Looks like a password prompt.
WvDial<*1>: Sending: (password)
WvDial Modem<*1>: % Authentication failed.
WvDial Modem<*1>: Username: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: daniel.b
WvDial Modem<*1>: daniel.b
WvDial Modem<*1>: Password: 
WvDial<*1>: Looks like a password prompt.
WvDial<*1>: Sending: (password)
WvDial Modem<*1>: % Authentication failed.
WvDial<Notice>: Don't know what to do!  Starting pppd and hoping for the best.
WvDial<Notice>: Starting pppd at Wed Nov  7 14:37:33 2007
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 8414
WvDial<*1>: Using interface ppp0


I know my username password and dial number are correct and it recognises my ISP
How do i fix this problem

---

### Post by NotTheMessiah on 2007-11-06
Open firefox and check if you have a working connection(after the ppp error) it must be a problem with your credentials or number

---

### Post by Bartender on 2007-11-07
I'd also try setting up pppconfig -
From what duncan has said, it seems to be the most reliable.  Directions for getting into pppconfig at the Modem Dial Up wiki
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

pppconfig can be a little awkward at first - it's all done on the keyboard, don't bother with your mouse, and there are a couple of parts I keep goofing up on.  When you get to Automatic or Manual DNS, you have to click down and tap a key (don't remember which one) to change it from Manual.
Also, at the username and password sections, don't forget to backspace to erase the existing text, then enter your values.

If you got it configured, you simply open a terminal and type pon
The modem should dial

Then there's a trick to the terminal screen - what is it?  I think you minimize that terminal screen, don't close it, and type poff to disconnect.

Anyways, try that, and also try editing your gnome-ppp and re-enter your username and password.  Close gnome-ppp, restart the PC, check to make sure the password looks right.  Another thing I've run into is some ISP's want just your username, others want username and domain.  You'll get an error similar to what you have if it's entered wrong. 

Hey, who's your ISP?  Most work with Linux but some don't.

---

