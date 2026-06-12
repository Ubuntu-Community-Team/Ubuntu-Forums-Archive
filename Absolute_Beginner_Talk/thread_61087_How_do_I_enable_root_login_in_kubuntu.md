---
title: "How do I enable root login in kubuntu?"
date: 2005-08-30
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-08-30
Root Login = Overrated *YES*

But Admin Mode is bugged, so is it possible to login as root in Kubuntu?

---

### Post by sneax on 2005-08-30
[http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

---

### Post by Muhammad on 2005-08-30
[QUOTE=sneax][http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)[/QUOTE]
 From the Login screen:

> root logins are not allowed

:/

---

### Post by sneax on 2005-08-30
Why do you want to login as root into the graphical user interface? You can't login as a normal user and do the root commands from a terminal?

---

### Post by FLeiXiuS on 2005-08-30
It's very dangerous to use the ROOT user account for anything other then making changes to the system.  Which should be done by the terminal.  Another thing, disabling the root account enables a lot of security benefits such as not being able to bruteforce the root account via SSH / Samba. 

My advice would be to leave it as is and just sudo when you need the root privledges.

---

### Post by Muhammad on 2005-08-30
I don't know how to edit my network settings by using the terminal yet.

Anyway, I found the solution:

```
sudo kwrite /etc/kde3/kdm/kdmrc
```
 Locate "AllowRootLogin"
 Replace "false" with "true"
 Logout then log in as root.

I hope this helps future generations of kubuntu users if they use the search function. :)

I have a new question, how do I add a network status indicator in the panel?

---

### Post by FLeiXiuS on 2005-08-30
man ifconfig
man ethtool

---

### Post by sneax on 2005-08-30
You are strongly advised not to login as root into the graphical user interface - you would forget you are root too fast and do foolish things like browsing the web etc... as root.

If you want to configure your network, read the howto's! I know it's not ideal but you're still using linux ;)

---

### Post by Lord Illidan on 2005-08-30
The terminal commands work, but using Kcontrol in adminstrative mode sucks. It requires you to be root to start with. Perhaps something can be done about this?

---

### Post by jingo811 on 2005-08-30
> you would forget you are root too fast and do foolish things like browsing the web etc... as root.

What's so dangerous about browsing the web as root?  Me new to Linux.

---

### Post by aysiu on 2005-08-30
[QUOTE=jingo811]What's so dangerous about browsing the web as root?  Me new to Linux.[/QUOTE] That means if something bad on the web breaches your system's security, it can do whatever root can do (i.e., everything). Isn't there some equivalent to the *gksudo nautilus* command in Ubuntu? Maybe something like *qtsudo konqueror* or just plain *sudo konqueror*?

---

### Post by racecat on 2005-08-30
[QUOTE=Lord Illidan]The terminal commands work, but using Kcontrol in adminstrative mode sucks. It requires you to be root to start with. Perhaps something can be done about this?[/QUOTE]

I don't remember what they were, but I've run into a couple of situations that require root permissions on the object of some function. but it wasn't possible to sudo it. My probably naive, but effective solution was to use chmod to change permissions on the file to allow everyone to write or execute, as applicable, then return it to normal when done. Oh, yea. I think on one occasion, I was saving a file I modified in a text editor.

Anyway, that was my simplistic solution to avoid logging in as root.

Bill

---

### Post by ericddobbs on 2008-01-16
This is the most annoying aspect of ubuntu/kubuntu. It seems that every time I want to do something, especially in a new installation, I have to sudo or kdesu. I don't care if it is dangerous to be root in the graphic mode. I am behind two firewalls anyway. I just want to be able to administer my system without being constantly nagged for a password in the graphic interface (KDE). For example, I wanted to view the contents of a mystery drive (a hard drive of unremembered provenance) and when I tried to view it in the graphical interface, I was told I did not have permissions to do diddly-squat. I don't remember the command line syntax for everything I want to find out (I first started experimenting with linux back in ninety-eight - the forum software turns a numeric number 8 into a smiley face in a date), so it is a pain to do this in a terminal, and I don't want to dig up the solutions in my numerous cryptic linux books. I just want to log in as root and be done with it. I like ubuntu/kubuntu, but if I am going to use linux on any of my machines, I must be able to log in as root in the graphical interface whenever I want to. If this is not possible, could you guide me to a distro that allows this? Will Fedora do it? If you don't want to post a public solution for this, would you please email me?[EMAIL="eric@ericdobbs.com"]eric@ericdobbs.com[/EMAIL] Pretty please with sugar on top? I am asking for a permanent solution that cancels the "root logins are not allowed" stone wall. If it must be configured at the terminal, that is fine. I started in the computer world in DOS, so the terminal doesn't scare me. It is just a pain in the patoot. I just would rather use root privileges graphically, because I am old and don't have much time left in which to be frustrated by leaving out or putting in a space. Please. Tell me. I won't tell anybody else; I promise.
Eric Dobbs

---

### Post by piobair on 2008-03-04
Vanilla Debian defaults to allowing root logins. I also want the answer to your question. I have been logging in as root since before Microsoft existed, so I don't need to be "educated" that root is dangerous.
Piobair

---

### Post by aysiu on 2008-03-04
> **piobair said:**
> Vanilla Debian defaults to allowing root logins. I also want the answer to your question. I have been logging in as root since before Microsoft existed, so I don't need to be "educated" that root is dangerous.
Piobair
Please don't revive old threads just to get on a soapbox you've already gotten on in another thread.

---

