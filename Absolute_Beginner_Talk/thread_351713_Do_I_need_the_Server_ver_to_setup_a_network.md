---
title: "Do I need the Server ver to setup a network?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by orcalover on 2007-02-02
Okay, sorry in advance if this should be obvious to me, but I'm VERY new to Ubuntu.

Currently we have Microsoft Small Business Server installed which controls our home office network (five PCs all together). We have a domain name (using DynDNS) that is also used for our email. 

I want to remove (kill sounds better, but...) windows (as well as burn every one of the windows install CDs in a bonfire to celebrate my liberation from windows hell) from every computer within my control and install Ubuntu desktop. I would like for all the PCs to be networked together, as well as have one of the machines host the domain name and handle our email. 

My question is, can I install the desktop version on all the computers, or do I need to install the Ubuntu Server on one of the machines, and have the desktop version running on the other machines. 

Thanks in advance, 

Sean

---

### Post by x64Jimbo on 2007-02-02
Will you be using the server machine as a workstation as well? If so, you'll still want to use the Ubuntu desktop CD. However, if all it's doing is serving the network and doesn't have to function as a workstation, you can install from the server CD because it doesn't include any window manager - it looks a lot like DOS when you use it. The benefit of using it in text-only mode is that it saves system resources for the more critical tasks.

---

### Post by Moldz on 2007-02-02
As far as I understand, the "Desktop" versus "Server" CD is basically the same thing.  The only difference is packages that are installed by default.  For example, the Desktop CD also installs a graphical environment.

Once you have Ubuntu installed, you have complete control over which software you can install.  You could turn a "Desktop" installation into a "Server" installation by simply adding or removing the appropriate packages.

So the short answer is yes, you can use the Desktop CD and install packages for networking such as file sharing services.

---

### Post by punx45 on 2007-02-02
my PIII is currently operating in a serverlike capacity.   it mainly serves files and http (with DynDNS pointing to it).  i started off with the standard Ubuntu install with gnome, but now it runs headless (although GDM is still running needlessly heh.)

so, you can go either way, as both (all, really) versions are very adaptable.   The decision really comes down to personal preference and hardware capacity.   Are you comfortable with the command line or do you prefer point and click?  Can your server handle a GUI and still run all the services you need without strain?

since you say you have already been using MS server editions, you probably won't have too much trouble with a graphical server.   the nice thing is that there are a few different choices in window management systems as well.   Ubuntu defaults with gnome, which my PIII can handle without too much hassle.   there is also XFCE which is much lighter (although it resembles Windows even less than Gnome or KDE).

if you have the time to play around I would suggest trying out a few options and see what you like.   You can even run live CDs on your server hardware and see how it performs.   Ubuntu will give you the Gnome desktop, xubuntu will give you the XFCE desktop, and there are plenty of more choices too.

---

### Post by orcalover on 2007-02-02
Thank you guys for the fast reply. I was pretty sure that the desktop and server versions were the same except for the default features, but I wanted to double check - still in that "too afraid to click or install anything" mode that window's puts you in.

Thanks again for the fast reply!

Sean

---

### Post by punx45 on 2007-02-02
yeah, so just to make sure we are clear, (so you dont end up with any nasty suprises)

the "Server" install is **command line only**.  So if you want to be able to use a mouse, go with the desktop version.

---

### Post by orcalover on 2007-02-02
Right, 

I want the GUI anyhow, but if I needed the server version I was just going to install it through APT, but starting with the desktop version is going to be much better. 

I actually have a VPS through a webhost that runs Ubuntu Server, so I have some experience with it, but I'm still a newbie to Ubuntu. I wish I would have switched over long ago, but I just kept thinking Windows would get better. I guess denial really is the first sign that you have a problem, lol. 

Thanks again, and I look forward to being an active participant in the Ubuntu community, as well as an advocate!

Sean

---

