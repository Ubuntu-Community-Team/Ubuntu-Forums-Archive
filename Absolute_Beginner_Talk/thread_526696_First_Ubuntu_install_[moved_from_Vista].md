---
title: "First Ubuntu install [moved from Vista]"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by He|iX on 2007-08-15
Hi, Ive just installed ubuntu and moved over from Vista.

Just a few questions. At work I use VisionApp Remote desktop to manage many RDP sessions at a time - is there anything I can use like this in Ubuntu?

There are many things on my Vista partition which I'm scared about not being able to use on Ubuntu, but for now 'll see how it goes!

---

### Post by skymera on 2007-08-15
you moved from Vista!!!1
that is the best decision you will ever make!

what stuff are you afraid about not being to use?

you can read/write to NTFS :)

---

### Post by neoguy2012 on 2007-08-15
Hmmm... if you click on the application menu -> Internet -> Terminal Server Client, I think you'll be able to connect to another computer via RDP in Ubuntu.  I never tested it out though.  I hope that helps!

---

### Post by dustrho on 2007-08-15
Go to the Synaptic Package Manager and download Gnome-RDP. It's a great tool that I use to manage the servers in my office. It allows you to store whatever servers you want, so all you do is double-click them and they open up an RDP session. You can even store a username & password, but I would advise against it because that's stored in clear text I believe.

Hope that helps.

---

### Post by He|iX on 2007-08-15
Gnome-RDP souds great, looks like I shouldnt have a problem working with RDP then!

Theres a few apps I use for Checkpoint, theres a client I hope will work with Ubuntu. Apart from that, I'm happy with the ubuntu install, even though I haven't used it before it feels good because of all the cisco stuff I have to configure ec.

Thanks for your help, any other apps you would recommend? I use PuTTY and stuff like that frequently too.

---

### Post by He|iX on 2007-08-15
Another thing too (probably the wrong place to post this though)

I still have vista on my T61p Laptop, four partitions:

1) swap
2) Ubuntu
3) data partition (ntfs from vista)
4) vista

That was the only way I could get ubuntu to install and dual boot - having vista in the last partition.

If ubuntu comes out with a new release, is it ok to blow away the second partition with ubuntu and reinstall (or upgrade) if I save all my junk onto the 3rd data partition which is from vista (ntfs)

Sorry if I sound like a noob So much work on my laptop, I'm stuffed if it all goes wrong, including the fact that its all working now from a fresh install, dual booting perfectly, but if I reinstall ubuntu/upgrade, it might stuff everything.

To be honest I still haven't even had time to install any drivers for either OS yet, as I am migrating Laptops too. So I hope the drivers will install fine for Ubuntu before I worry too much about blowing away partitions for upgrades.

---

### Post by obscur156 on 2007-08-15
Nice move you just did by trowing out vista.
You wont regret it,of course you will have to learn but its not that hard and the ubuntu community is great and always willing to help.

Have fun with your new distro.  :)

---

### Post by He|iX on 2007-08-15
Cheers,

I didnt really throw it out, its still there in case I totally stuff things up lol.

Just got to figure out how to install all the drives, apps and stuff I need to get working again! So used to just double clicking exe files to install drivers. 

I'm even worried I wont know how to join a domain with Ubuntu too lol

---

### Post by dustrho on 2007-08-15
I'm not in the office right now, but I don't think I did anything to configure my desktop in regards to connecting to our domain. I think it was just automatic for me. I work as a Security Administrator, and everyone on my team has gone away from Windows. Well, I have one laptop running Windows XP, but that's more for Visio, Acrobat and Photoshop when needed. If you're using Checkpoint, our firewall admin just RDP's into the firewall management server to do all his work. On my desktop I use the following:

- OpenOffice for all documentation
- Gnome-RDP for connecting to other servers
- Konqueror for the limited FTP work
- PuTTY on occasions

There's others but I just can't remember the names of them, as I've only been using it at work for the last month or so.

What kind of work do you do? Obviously some networking but more on the infrastructure side or security side?

---

### Post by He|iX on 2007-08-15
Well, Im a Network systems Engineer, so I do pretty much everything from Business as usual to projects

Thanks for your recommendations above - I think this is pretty much everything I need to work. As long as I can RDP and telnet/ssh everywhere should be good. 

There are other applications that I need, but they use Java for device monitoring - these no issues with this I hope; well soon find out.

---

