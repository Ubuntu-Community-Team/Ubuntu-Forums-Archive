---
title: "Download a firewall vs apt-get"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by florida490 on 2007-06-24
Hello,
I installed the Firestarter firewall front-end using apt-get.  The installation went fine, but I'm concerned about going on the Internet with no firewall to install a firewall.  Seems insane to me. Is there a way to download the actual program file for Firestarter and burn it to CD so that I don't have to access the Internet to install it?

---

### Post by Malibu Illusion on 2007-06-24
Firestarter is merely a GUI frontend for iptables, which is installed by default.  Ubuntu machines are already protected by iptables without Firestarter; Firestarter just allows you to specify rules and whatnot via the GUI.

---

### Post by florida490 on 2007-06-24
This iptables program, how do I know it is working?  If there are no permissions set, is there any chance of blocking an intrusion on my computer?

---

### Post by southernman on 2007-06-24
Yeah, what ^^ they said. ;)

I tried to get amule working last night, thought installing firestarter was the answer. NOT. I managed to google, finally hitting the write keywords and learned a little about iptables... enough to open the ports needed opening. The same way I've learnt 99.9% of what knowledge I have for Ubuntu came from google and searching these fine forums.

Don't worry... your heavily guarded running Linux. Just don't be an I-D-10-T; and I say that in the nicest way you could mean it, and you'll be ok.

Enjoy! ;)

---

### Post by kevdog on 2007-06-24
Iptables works by default -- basically all incoming ports are closed by default in linux -- as opposed to windows where they are all open.  Firestarter or another program known as Guardog (another GUI based program to manipulate the iptables file) then allow you to open certain ports on a custom basis, depending on your needs.  I use guardog, a lot of people here use firestarter.  I dont think it matters, because both basically just configure the iptables file.  Neither program needs to be running in the background, because the OS/iptables functionality is built-in.  The only time either program needs to run is when manipulating the firewall rules. Got it??!

---

### Post by Megaqwerty on 2007-06-24
First of all, Ubuntu comes standard "locked down" it has it's own firewall called "iptables" which will keep you safe unless you purposly open those ports (if you got an ftp server package for example) so you are completely safe downloading firestarter with apt-get. However, I understand your need to feel totally secure, so here is how you would download the actual program and burn it to a CD. I'm assuming you are accessing it through a different computer, or through Windows on the same computer. I'm not going to teach you how to burn a CD, as I assume you know how.

You can download Firestarter from [www.packages.ubuntu.com](www.packages.ubuntu.com) download it, and merely double click on the .deb file it to install. However, it might complain that certain dependencies aren't met. It will list that package you need, and you can go back to the page where you got Firestarter and download that other program that it is requesting. Once again, you may have to go back again if that program needs another program for it to work. This is something that apt-get prevents called "dependency hell" however, since you are doing it by hand, instead of using apt-get, aptitude, or synaptic, you are at risk to fall victim to this cycle of checking dependencies, and resolving them, until all dependencies are satisfied. 

So once again, I will say: You are safe going on the internet from a fresh install of Ubuntu, don't worry about it. The ***only*** reason I have Firestarter is so that I can *open* ports on my Ubuntu computer. You will find that Ubuntu is a very secure Operating System, and the only reason I detailed the process of installing Firestarter from a downloaded file is to show you it *is* possible if you have the time to deal with any dependency issues that may or may not crop up.

Good Luck,

Megaqwerty

EDIT: Apparently while writing my lengthly response, people beat me to it :-). But I stress again that you are completely safe by default due to iptables.

---

### Post by southernman on 2007-06-24
> **florida490 said:**
> This iptables program, how do I know it is working?  If there are no permissions set, is there any chance of blocking an intrusion on my computer?Are you behind a router? Which you know is a hardware firewall in and of itself.

To test and see how vulnerable you may be... [go here]("https://www.grc.com/x/ne.dll?bh0bkyd2"). Shields up is a pretty solid test / scan. Informative as well.

---

### Post by Malibu Illusion on 2007-06-24
> **florida490 said:**
> This iptables program, how do I know it is working?  If there are no permissions set, is there any chance of blocking an intrusion on my computer?

If there are no permissions set, and all your ports are closed, what do you have to worry about to begin with?  The only opportunity for intrusion is by exploiting a service running and listening on an open port.  Ubuntu, by default, comes with none unless you configure them and, even then, you'd either have to poorly configure said daemon or run a version with security vulnerabilities in order to put yourself at risk.  A firewall wouldn't help you in this case as you'd have likely permitted traffic at the port in question anyway.

A computer connected to the internet is as safe as the daemons that it has configured to listen on ports.  Ubuntu comes with none of these out of the box.  You have nothing to worry about.  Windows, on the other hand, has all sorts which cause a plethora of problems.  This isn't Windows.

---

