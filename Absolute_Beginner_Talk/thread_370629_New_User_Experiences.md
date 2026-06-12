---
title: "New User Experiences"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by bexpert on 2007-02-25
I've just made the switch to Xubuntu, and I have mixed feelings.

The pros:
1) It installed reasonably well (it only took three times)
2) It's fast enough on my old laptop (G3 iBook)

The cons:
1) I have no idea what Gnome and KDE are, how they relate to Xubuntu, or why they seem to be necessary sometimes, started sometimes, and not necessary sometimes. This stuff is confusing. Don't blame me. It's not my problem that it's incomprehensible to noobs.
2) I would like Flash and JRE to work out of the box. I know, licences blah blah blah. Still, I can't install them. I have no idea how to. See 3.
3) While the "Add/Remove Programs" idea is brilliant, I can't find the ones I need. Where are they? Am I missing something?
4) Support is sometimes very rude. I posted to the IRC. Of three responses, two were the usual 'Frak off noob' kind of stuff.
5) The power management on my laptop isn't working. I liked being able to shut it and have it sleep. 
6) I still need to use the command line, apparently. I hate the command line. I hate it a lot.

Look, I like (X)Ubuntu. I'm amazed at how well it works, and how little it costs. It's great. Honestly. There are just a few things a switcher practically needs. 

Adam.

---

### Post by aysiu on 2007-02-25
> **bexpert said:**
> 
1) I have no idea what Gnome and KDE are, how they relate to Xubuntu, or why they seem to be necessary sometimes, started sometimes, and not necessary sometimes. This stuff is confusing. Don't blame me. It's not my problem that it's incomprehensible to noobs. Well, Gnome and KDE give you a different look and feel. You may see some Gnome-related stuff because Gnome and XFCE are built with the same toolkit (GTK). Also, during boot-up, you may see that the Gnome Display Manager is starting--that's just what manages the login screen. XFCE doesn't have its own display manager. > 2) I would like Flash and JRE to work out of the box. I know, licences blah blah blah. Still, I can't install them. I have no idea how to. See 3. You may be interested in Linux Mint or Mepis, then. Those are Linux distributions based on Ubuntu, using Ubuntu repositories, but with a lot of proprietary software included by default. Licenses sometimes have to do with it, but for Ubuntu it's mainly to do with ideology. > 3) While the "Add/Remove Programs" idea is brilliant, I can't find the ones I need. Where are they? Am I missing something? This may help:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Edit**: Since you apparently hate the terminal, use this link instead, then:
[http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories) > 4) Support is sometimes very rude. I posted to the IRC. Of three responses, two were the usual 'Frak off noob' kind of stuff. Don't use IRC. Use these forums instead. > 5) The power management on my laptop isn't working. I liked being able to shut it and have it sleep.  What model laptop do you have? > 6) I still need to use the command line, apparently. I hate the command line. I hate it a lot. You don't *need* to use the command-line. People will just recommend you use it because it's efficient, uniform, and more informative if something goes wrong.

---

### Post by bexpert on 2007-02-25
Well, that's very helpful. 

A bit more on 1), if you could:
Will KDE and Gnome applications run on Xubuntu? I've tried a few, and some seem to. Others don't. It's never particularly clear whether it's because I have a PPC chip or because I have Xubuntu.

And about the command line:
I'm not sure how to get around it. I tried downloading Flash from Adobe. I got an archive. I unzipped it, and, well, there it sits. The Adobe website says I have to log in, change directories, switch permissions--and I think that by the time I do this, I will end up with a brick for a computer. 

Is there some way around this? It does seem to be the archives that are the sticking point.

Thanks very much.

Adam.

---

### Post by aysiu on 2007-02-25
> **bexpert said:**
> 
A bit more on 1), if you could:
Will KDE and Gnome applications run on Xubuntu? I've tried a few, and some seem to. Others don't. It's never particularly clear whether it's because I have a PPC chip or because I have Xubuntu. You're right on. All KDE and Gnome applications should run in Xubuntu. In fact, any application you can run in any environment will also run in any other environment. But you're also right that there are certainly applications not designed to run on PPC--this is completely environment-independent.

> And about the command line:
I'm not sure how to get around it. I tried downloading Flash from Adobe. I got an archive. I unzipped it, and, well, there it sits. The Adobe website says I have to log in, change directories, switch permissions--and I think that by the time I do this, I will end up with a brick for a computer. 

Is there some way around this? It does seem to be the archives that are the sticking point. Well, since you hate the terminal right now (I hope you'll grow to love it eventually), the easiest way to install Flash is to visit a website that requires Flash. Firefox will then tell you a plugin is missing. Just click to install the plugin and click all the appropriate Next buttons, and it should install.

If that doesn't work, copying and pasting these commands will help:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

You may also want to read (for things other than Flash), these two links:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Maestro23 on 2007-02-26
Some sites to intro you to Linux command/file structure:

LinuxCommand.org: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

TuxFiles(For the Linux Noob): [http://www.tuxfiles.org/](http://www.tuxfiles.org/)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Great All-Around Ubuntu source: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

*Also a link in my sig to the Ubuntu guide and a thread called "Is Ubuntu for You?"

Good luck if you decide to stay.

---

### Post by bexpert on 2007-02-26
Many thanks!

Following your advice, I opened up terminal and gave some of your recommendations a shot--it seems that as long as I can cut and paste someone else's work, I do OK.:) 

Perhaps, as you say, I will come to love the terminal. I used to love WordPerfect 5 and DOS, so it's not inconceivable. 

Alas, the Firefox plug-in method hasn't worked. I don't know why, but it's failed me both for Flash (Youtube) and Java Run Time Environment (ThinkFree.com). Flash takes me, eventually, to Adobe, and they're not helpful. JRE deadends. I'll live without for now.

Anyway, you've been more than helpful. Many thanks.

Adam.

---

### Post by aysiu on 2007-02-26
The Java installation failure doesn't surprise me, but the Flash one does.

I'll tell you that when I tried to use Ubuntu for the first time (in April of 2005), all the terminal commands I was given were a total turnoff for me. I ditched Ubuntu quickly in favor of Mepis. One month later, I switched to Ubuntu and have stuck with it ever since... and grown to love the terminal.

So who knows?

---

### Post by Meson on 2007-02-26
I had never used linux at home before two (maybe three) days ago.  Just in a server and programming environment via SSH.  The amount of active members on this forum is unbelievable.  Almost all of my needs have been addressed EXTREMELY quickly, almost as if this was meant to be a real time medium.  I'm so comfortable at this point that I rearranged my partitions and installed Ubuntu as my primary installation.  I've only logged back onto windows once to move my files over the network to the shared partition.

It's worth sticking with (and btw, I find gnome a little smoother and easier to use than KDE).

As for Java.  Enable the multiverse packages in the software sources window.  Then do a search in synaptic for JRE and install the sun-* stuff.  The browser plugin is listed there as well.

Windows free for 2 days and counting. . .

---

### Post by undertakingyou on 2007-02-26
Another thought for Flash and JRE is to install AUTOMATIX and just tell it to do it.  They have a .deb file on their website that will do all the install stuff of automatix for you.  Then when you run automatix, it is like the add and remove programs.  Just check a box and hit install.

---

### Post by aysiu on 2007-02-26
Here's a link:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by jkeyes0 on 2007-02-26
> **Meson said:**
> I had never used linux at home before two (maybe three) days ago.  Just in a server and programming environment via SSH.  The amount of active members on this forum is unbelievable.  Almost all of my needs have been addressed EXTREMELY quickly, almost as if this was meant to be a real time medium.  I'm so comfortable at this point that I rearranged my partitions and installed Ubuntu as my primary installation.  I've only logged back onto windows once to move my files over the network to the shared partition.

It's worth sticking with (and btw, I find gnome a little smoother and easier to use than KDE).

Windows free for 2 days and counting. . .

Congrats Meson. I'm in the same boat. I started with Slackware about 6 years ago, off and on, using Mandrake, Red hat 6, 7, 8, and 9, Fedora, Lycoris, Linspire/Lindows, and finally found Ubuntu. I first tried it around 4.07, but I came back around 6.06, because my "windows" needs dwindled, and now the only thing I need windows for is Nortel VPN connectivity. I've converted both my laptop and desktop to Ubuntu, and I'm not looking back. VMware will handle the VPN thing for now.

bexpert: I've been frequenting the forums alot more lately, and you really get a mix there. I've given as many helpful responses as I can. In your case, if you're uncomfortable with the command line, and just want to get things installed so you can start working with Ubuntu, you might try a utility like Automatix2 or Easyubuntu. Search the forums for more information. Note: These programs are not officially supported by the forum staff, but you can find some useful articles if you have trouble with them within the forums here.

---

### Post by energiya on 2007-02-26
If Automatix doesn't work as it should (it didn't for me), you could always try [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy"). Its very usefull.

---

