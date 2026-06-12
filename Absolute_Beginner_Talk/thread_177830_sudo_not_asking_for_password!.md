---
title: "sudo not asking for password!"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by ImplicitProcrastination on 2006-05-16
somehow i managed to make sudo not ask for a password anymore.

I'm no expert, but this strikes me as a really big, scary, security hole. Especially considering my password just randomly changed on me and I had to get a root screen from recovery mode and change it back.

Any idea what I did?

---

### Post by nanotube on 2006-05-17
[QUOTE=ImplicitProcrastination]somehow i managed to make sudo not ask for a password anymore.

I'm no expert, but this strikes me as a really big, scary, security hole. Especially considering my password just randomly changed on me and I had to get a root screen from recovery mode and change it back.

Any idea what I did?[/QUOTE]

well, first, if your password "randomly changed" on you, and you havent done anything to cause it, i would be asking myself if my computer has been hacked. are you by any chance running any services on your comp that are open to the world? like apache, ssh, telnet, ftp? 

now, about sudo preferences, easiest way is to use command
```
sudo visudo
```
and edit your sudoers file. see if there is a NOPASSWD in there somewhere.
actually, just post the contents of your /etc/sudoers file (the same one that's being edited by the previous command) and we will take a look.

---

### Post by ImplicitProcrastination on 2006-05-17
Here is sudoers.

That's exactly what I was asking myself, that's why I'm so concerned.

Being a CS student I constantly use ssh. Thanks to your response I realized that (for some reason, I think it's related to a word translation program I had been running) I do have apache installed. Not anymore.

Thanks for your quick response. What follows is my sudoers:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```

---

### Post by Jussi Kukkonen on 2006-05-17
> Especially considering my password just randomly changed on me
Passwords don't get changed by themselves, you should really consider your machine compromised -- changing your password later is not going to make it safe again. 

Your /etc/sudoers looks fine, btw.

---

### Post by akudewan on 2006-05-17
Sudo may remember your password for a few minutes and not ask you again & again. Try after 3 minutes.

Your password randomly changed? Then this may be a bigger problem...:confused:

---

### Post by ImplicitProcrastination on 2006-05-17
How big of a problem do you think? Could I get arrested?

If nothing much will come of it then I think I'll just wait and do a fresh install of dapper.

It's still odd that sudo no longer asks for a password.

Might there be anyway of telling what my computer has been used for?

---

### Post by gr0kzer0 on 2006-05-17
> How big of a problem do you think? Could I get arrested?


It depends.  If the person who compromised your box used it to commit a crime, and the polica trace it to your computer, you're gonna have to prove it wasn't you.

> Might there be anyway of telling what my computer has been used for?

Your bash history file might show you what's been done with your box.

---

### Post by ImplicitProcrastination on 2006-05-17
Figures this should happen during exams...

---

### Post by skippy81 on 2006-05-17
[QUOTE=gr0kzer0]It depends.  If the person who compromised your box used it to commit a crime, and the polica trace it to your computer, you're gonna have to prove it wasn't you.[/QUOTE]

Nope, they (the police and CPS) have to prove beyond reasonable doubt that it was you.  :cool: 

When your machine gets hacked legal consequences arn't really much to be worried about.  I find it hard to believe that your machine was hacked at all to be honest.  If you were running SSH its no big deal, a hacker would have had to brute force your admin password.  Unless he knew your user name this would be hard.  Brute forcing root is impossible AFAIK on ubuntu, I think by default root isnt even set.

Have a look through your log files.  If you have ssh installed then you should have an ssh specific log somewhere.  Most of the logfiles can be found in /var/log/ i believe.

---

### Post by gr0kzer0 on 2006-05-17
Skippy, the assumption of innocence is in /court/.

The OP asked if he could be arrested.  If the police traced a crime to his computer, he'd have to convince them that he didn't do it, or they'd arrest him.

Sure, the burden of proof is on the prosecution. But to make the arrest, all the police need is suspicion.

---

### Post by ImplicitProcrastination on 2006-05-17
What's an OP?

Although I appreciate the knowledge of how to check mty logs, how do I know that you (skippy) aren't the one hacking my box? I'm not accusing you of anything, most likely your intentions are good because I've seen you help out many people on these forums but my point is how's one to know?

Maybe I will reinstall sooner.

---

### Post by nanotube on 2006-05-17
OP = original post[er] (in this case - that's you)

yes, your sudoers file looks just fine, no changes from default.
but note that once you use sudo, there is a time period of 15 minutes that you can use sudo again, without entering password. (i assume that time period has passed by now :), but still, just to let you know). 

if you had things other than ssh running (like apache with some stuff thrown on top, or sendmail, or whatever), it is not beyond reason to suspect you may have been hacked. ssh is very solid, but other stuff is not so much. although even ssh can be hacked by brute force, or if you have a very guessable password. (also, if there was a keylogger on the remote machine that you used to ssh into your machine, your password may have been compromised that way).

but yes, if you have any doubts, back up all your files, wipe the drive and reinstall from scratch. and don't run any services except for ssh after that, and make sure to have a strong password, and don't log in from remote computers that you do not trust. (best way would be to use ssh key authentication to log in from remote machines - and carry that key around on a usb stick).

as to log checking - there is a lot of logs in /var/log, you can snoop around in there and see if there is anything out of the ordinary.

other notes: check to see if anything is listening on any ports (use command "sudo netstat -plant"). on your new install, make sure to install a simple firewall ruleset that blocks incoming stuff (except for ssh, if you run that). for a simple but effective iptables ruleset, see the first link in my sig, and go to the firewall section.

---

### Post by steve.horsley on 2006-05-17
**sudo netstat -plantu** might be better. You can't rule out UDP control ports.

---

### Post by nanotube on 2006-05-17
[QUOTE=steve.horsley]**sudo netstat -plantu** might be better. You can't rule out UDP control ports.[/QUOTE]
good point. :)

---

### Post by ImplicitProcrastination on 2006-05-18
Oh.
Holy shit.

There seems to be a few things listening:

```
tcp        0      0 127.0.0.1:32769         0.0.0.0:*               LISTEN     7332/hpiod         
tcp        0      0 127.0.0.1:32770         0.0.0.0:*               LISTEN     7349/python        
tcp        0      0 0.0.0.0:2628            0.0.0.0:*               LISTEN     7387/0             
tcp        0      0 0.0.0.0:5190            0.0.0.0:*               LISTEN     8336/reaim         
tcp        0      0 0.0.0.0:1863            0.0.0.0:*               LISTEN     8336/reaim         
tcp        0      0 0.0.0.0:1864            0.0.0.0:*               LISTEN     8336/reaim         
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     9517/cupsd         
tcp        0      0 0.0.0.0:538             0.0.0.0:*               LISTEN     7582/gdomap        
tcp        0      0 0.0.0.0:4443            0.0.0.0:*               LISTEN     8336/reaim         
tcp        0      0 0.0.0.0:5566            0.0.0.0:*               LISTEN     8336/reaim         
tcp        0      0 132.162.218.229:55450   63.236.73.208:80        TIME_WAIT  -                  
tcp        0      0 127.0.0.1:32769         127.0.0.1:47744         ESTABLISHED7332/hpiod         
tcp        0      0 132.162.218.229:48193   216.155.193.160:5050    ESTABLISHED8875/kopete        
tcp        0      0 132.162.218.229:60865   205.188.9.132:5190      ESTABLISHED8875/kopete        
tcp        1      1 132.162.218.229:37919   66.216.68.48:80         CLOSING    -                  
tcp        0      0 132.162.218.229:37916   66.216.68.48:80         TIME_WAIT  -                  
tcp        0      0 132.162.218.229:57254   132.162.1.218:110       TIME_WAIT  -                  
tcp        0      0 132.162.218.229:45512   207.46.114.113:1863     ESTABLISHED8875/kopete        
tcp        0      0 127.0.0.1:47744         127.0.0.1:32769         ESTABLISHED7349/python        
tcp        0      0 132.162.218.229:35667   63.236.73.159:80        TIME_WAIT  -                  
tcp        1      1 132.162.218.229:52219   82.211.81.186:80        CLOSING    -                  
tcp        0      0 132.162.218.229:42726   62.70.27.118:80         TIME_WAIT  -                  
tcp        0      0 132.162.218.229:42724   62.70.27.118:80         TIME_WAIT  -                  
tcp        0      0 132.162.218.229:42725   62.70.27.118:80         TIME_WAIT  -                  
tcp        0      0 132.162.218.229:43797   66.225.202.210:80       TIME_WAIT  -                  
udp        0      0 0.0.0.0:538             0.0.0.0:*                          7582/gdomap        
udp        0      0 0.0.0.0:68              0.0.0.0:*                          7323/dhclient3 
```

What's ssh key authentication?

Is there anyway if I backup some of my stuff first that the hacker could gain re-entry?

Sorry but I've been kind of stupid lately, exams and long nights dude...

---

### Post by ImplicitProcrastination on 2006-05-18
Oh, but those are TCP ports...


So I looked at some of the log files.

What exactly am I looking for?

---

### Post by steve.horsley on 2006-05-18
I don't like the look of that. Anything listening on 127.0.0.1 is safe, but there are three that look suspicious to me: 

0 - That's an odd process name. I don't trust it
reaim - it's an instant messaging relay, apparently
gdomap - something to do with network remote execution? Not sure.

If you don't know you are running these, I think you can assume you've been hacked. Back up your data files and reinstall from scratch. Change all passwords. If you've ever typed credit card details in, assume they're public knowlege now.

---

### Post by Mustard on 2006-05-18
What would be interesting to look at is your .bash_history files for your user and for root.  The first is found in your users directory, the second is found in /root.  The .bash_history file shows a record of what commands have been used last in the bash shell.  If you see commands that have been issued in the .bash_history that are suspicious, ie you never made them, or they are doing things that seem out of place, then that would be a good sign that someone other than yourself has been executing commands via the bash shell.  It's always possible that the .bash_history files were deleted after the fact, by whomever may have been using the bash shell.

---

### Post by Anduu on 2006-05-25
OK I was having the exact same problem.

First make sure you are not in the sudo group.

Now run Users and Groups and find your user name.Click Properties.Click the Advanced tab.There is a section called Main Group with a drop down box.In the box mine said sudo.I changed it to admin and now sudo works.

Hope this helps.

---

