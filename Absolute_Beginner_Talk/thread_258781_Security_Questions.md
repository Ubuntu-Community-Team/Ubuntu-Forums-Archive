---
title: "Security Questions"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Regord on 2006-09-16
I'm a noob to Linux and just installed Ubuntu.  I currently have the desktop version running behind a router device (belkin) that has a built in firewall and it's doing NAT.  

Should I take additional steps on the Ubuntu machine to ensure I'm protected?  The Ubuntu install doesn't appear to have installed any sort of firewall or virus scan software.  This concerns me because I'm used to having these things on my Windows box.  

Any suggestions??

Thanks!

---

### Post by Imsati on 2006-09-16
As far as virus software is concerned, you'll me more than fine without. If you share files with Windows users (home networks, e-mail, etc.), you may want to install a package just to you don't inadvertantly send them anything, but for the most part, windows-based viruses can't do much harm here. (Linux stability is the main reason I switched from XP)

---

### Post by Regord on 2006-09-16
Hmm...so are you saying that most people with Ubuntu don't run any sort of Firewall or Virus Scan programs??  Is that really a sound policy in this day and age???

---

### Post by xpod on 2006-09-16
Ubunto does have a firewall built in does it not?
You can get the frontend for it in the form of "firestarter" if you like.

Am i correct?

---

### Post by Regord on 2006-09-16
> **xpod said:**
> Ubunto does have a firewall built in does it not?
You can get the frontend for it in the form of "firestarter" if you like.

Am i correct?

Hey thanks!  I don't know if the FW is built in or what...I'm such a noob. :)  But I got that installed and I gues the FW is up and running. 

So now how about virus scan, is there a preferred program for Ubuntu?

---

### Post by Imsati on 2006-09-16
>So now how about virus scan, is there a preferred program for Ubuntu?

[http://www.ubuntuforums.org/showthread.php?t=121766](http://www.ubuntuforums.org/showthread.php?t=121766)

Above link will tkae you to a small discussion from months back (2-3 posts). Personally, I don't have any AV with Kubuntu, nor do I plan on installing any. In short, Windows (any version) viruses can't infect Linux.

However, that being said, recall what I posted before about sharing files with Windows PC's. If you transfer files or e-mail friends, grab one. The link just has what other people use. I haven't installed either of them , so I can't help you with that, although I'd imagine just search the Repository and Request Install.

---

### Post by towsonu2003 on 2006-09-16
> **xpod said:**
> Ubunto does have a firewall built in does it not?
You can get the frontend for it in the form of "firestarter" if you like.

Am i correct?
it has iptables but it is not configured, which means it does not have a configure firewall from a fresh install. but it does not have a service listening to the internet, so it is not really necessary. 

firestarter is a nice tool to configure your iptables (and thus have a software firewall). 
> **Regord said:**
> 
So now how about virus scan, is there a preferred program for Ubuntu?
you can check out clamav. launch synaptic (package manager) and search for clamav. 

If you are paranoid enough, check out this one as well: [rootkits]("http://en.wikipedia.org/wiki/Rootkit")(note: use a livecd to check for rootkits)

PS. you might wanna read documentation about [firestarter]("http://www.fs-security.com/docs.php") and [clamav]("http://doc.gwos.org/index.php/FirewallAntivirus") while using them. 


PSS. I use Ubuntu as a regular desktop box. I see antivirus and firewall applications as waste of resources in desktop (ie. not server) Linux, although I have firestarter bc I am a little paranoid, but have no anti-virus application. Instead, I tell people to whom I send files to make sure to scan my files bf opening them (even my email signature says so). And I scan them myself in my Windows thingy (dual-booting) if I transfer files from Linux to Windows.

---

### Post by xpod on 2006-09-16
Being as i dont use pc`s for anything important(other than learning how they work)i dont really care one way or the other now in Ubunto.....I had enough of that nonsense during my few months of windows to last me a lifetime.

So without any anti virus on here it`ll be good to see if anything EVER does get on......which i very much doubt it will?:twisted:

EDIT:i do actually have the firestarter

---

### Post by steve.horsley on 2006-09-16
> **Regord said:**
> Hmm...so are you saying that most people with Ubuntu don't run any sort of Firewall or Virus Scan programs??  Is that really a sound policy in this day and age???

I can't think of a good reason to use either at the moment. "Because Windows needs them" is not a good reason.

You don't need a firewall to control incoming connections because the default Ubuntu install isn't running any services - it doesn't accept incoming conections anyway. So until you install a service in Ubuntu you have no use for a firewall. Of course if you do nstall a service, then you may well want a firewall to control who can connect to it.

You don't have any use for a virus scanner unless you want to make sure you don't allow files infected with windows viruses to pass through your hands to other windows users. Bear in mind that virus scanners can only scan for known viruses. And there are no Linux viruses in the wild, so nothing for a Linux virus scanner to look for. That could change tomorrow of course if a Linux virus were to break out, but a virus scanner written today would not recognise it.

---

### Post by Regord on 2006-09-16
Thanks for all the responses!  It's good to know that VS and FW aren't as necessary as in the MS world.  

My goals for this install are to mainly test things and learn Linux and all sorts of other programs.  I'm prolly going to use it as a print server, Web Server (but not for the rest of the world...just to learn about PHP, MySQL, Perl, Java and other things).  I'm planning on allowing only SSH and SFTP connections from my windows box.  I'll be transferring files to and from my Windows machine and I guess I just assumed that since they are intel CPUs that they'd be open to the same types of viruses....but I guess it's not so much the hardware that's at risk as the OS.

Basically I'm trying to recreate the development and web server computers that are available through my University.  I'm not yet comfortable dropping my Windows machines because in the past, I've had some serious problems with Linux...granted I've never used Ubuntu.

I guess the reason I'm a bit paranoid is I've been burned in the past by people that said "don't worry, everything is fine" only to find out everything is NOT fine...in fact they are anything BUT fine.  This didn't have so much to do with Linux or even computers but I've heard this before with some significant consequences.

---

### Post by psycosmyth on 2006-09-16
ok, viruses are not much of a worry, no problem, but the worry of being hacked is another. I use firestarter for sure and aliases like crazy but can I be secure from spies? Not that I'm worth the trouble.In the Linux communith it seems like a brotherhood, most of the time other users will see that you use it too and be cool with it.

---

### Post by towsonu2003 on 2006-09-16
> **Regord said:**
> 
My goals for this install are to mainly test things and learn Linux and all sorts of other programs.  I'm prolly going to use it as a print server, Web Server (but not for the rest of the world...just to learn about PHP, MySQL, Perl, Java and other things). I'm planning on allowing only SSH and SFTP connections from my windows box.
Good idea to use a firewall with these services running :)

> but I guess it's not so much the hardware that's at risk as the OS.viruses are most usually OS-specific. some aren't, and there _are_ viruses / rootkits for linux (though I never came accross a linux user who got infected). so, you still have to be careful (like not downloading everything you see, not using root privileges etc). Also, make sure you have a good anti-virus program in your Windows box (as you'll be transferring files over there).

---

### Post by Regord on 2006-09-16
Aliases??  hmm...I'll look into those.  Not sure what they are tho.

Towsonu2003 Yes, I've got a good VS and FW on my Windows box.  It's trapped every virus that tried to launch and I keep it updated so I think that machine is clean.

Ok so I just double clicked the firestarter icon and it asked me for the p/w then said starting firestarter.  So is the firewall launched on boot or only when I launch firestarter?

---

### Post by towsonu2003 on 2006-09-16
> **Regord said:**
> 
Ok so I just double clicked the firestarter icon and it asked me for the p/w then said starting firestarter.  So is the firewall launched on boot or only when I launch firestarter?
If you are using only one interface (ie not switching between network cards like wired than wireless etc) and if it is not dial up, it will start when comp boots. you can always check with ```

sudo /etc/firestarter/firestarter.sh status
```
You still have to configure it under "Policy" in the GUI... 
I personally prefer to choose "restrictive by default" for "outbound connections" and then add ports as I need them (port 80 is http, port 443 is https, and you'll need those in your outgoing connections). 

If you find out that you have to start firestarter gui on every boot, this will start it as well: 
```
sudo /etc/firestarter/firestarter.sh start
```

---

### Post by Regord on 2006-09-17
cool thanks towsonu2003

---

### Post by steve.horsley on 2006-09-17
> **Regord said:**
> My goals for this install are to mainly test things and learn Linux and all sorts of other programs.  I'm prolly going to use it as a print server, Web Server (but not for the rest of the world...just to learn about PHP, MySQL, Perl, Java and other things).  I'm planning on allowing only SSH and SFTP connections from my windows box.  I'll be transferring files to and from my Windows machine and I guess I just assumed that since they are intel CPUs that they'd be open to the same types of viruses....but I guess it's not so much the hardware that's at risk as the OS.

That's good reason to use both a fw and a vs. The fw can keep the unwashed masses from connecting to your servers, and the vs can help keep your archive of windows files clean. Windows viruses can't hurt Linux, but you don't want to use Linux as a Windows virus warehouse.

---

