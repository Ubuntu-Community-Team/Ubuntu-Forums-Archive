---
title: "Terminal Services/VNC from Windows to Linux"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Trebek on 2007-05-11
Ok here is the deal:  Im a new linux user, completely blind to how linux works.  I have just put Ubuntu on my home desktop.  I have a laptop i use @ work with Win XP pro on it, which i use VNC to remote to our users for support. (VNC version 3.3.5 if that matters) and I also use Terminal Services.  

What I want: 

I want to be able to remotely access my home desktop (through a linksys wrtg b/g router) from work, or wherever so i can tool around with linux on my free worktime here.  I have a basic idea of what i need to do/know, just not enough details to implement this. 

I know that i need:
1. Router set up to port forward (need to find out VNC's port #)
2. PC set to allow incoming requests from VNC (with a password of course)

that's about it.  I know i have VNC installed on my machine, but i cant find it.  I am so used to the installed programs putting a shortcut on the desktop, i have no idea where to find my installed programs.

---

### Post by lazyart on 2007-05-11
On your Ubuntu box, go to System>Preferences>Remote Desktop and enable viewing of your dekstop on remote control.  Check the require password box and add a password.

On your router, be sure that port 5900 is allowing traffic to your desktop.

Now all you have to do is know your IP address and you can VNC into your desktop.

Oh, you don't know your IP?  An option is to create a free account somewhere that will translate your dynamic IP to a static name.  [www.dyndns.org](www.dyndns.org) is what I use.  You'll have to install a client on your desktop that will notify dyndns when your IP address has changed.  Check the repositories-- there are a few options.

Another way would be to use Hamachi to create a VPN with your desktop and laptop both on it.  Then they can see each other using an address like 5.0.0.x or something like that.  If you have a Windows machine at home (and this is how I do it):

Create an account a logmein.com.  Install their client onto the windows machine.
Log into your logmein account, then use it to view your windows machine.  From that, VNC to your Ubuntu box.  A bit strange, but it gets around closed ports because it only uses port 80 externally.

---

### Post by Trebek on 2007-05-11
what would be faster/better?  Basically, nobody will be on my PC when i will be connecting to it remotely, just lookin for a way to operate my PC from work, and access my files, etc from my laptop no matter where i was.

---

### Post by lazyart on 2007-05-11
By using logmein you don't have access to your files, but you do have access to your desktop.  Hamachi is a cool way to do it because it's like the machine are all on the same network (hence VIrtual Private Networking) but I would suspect that your company would frown on you having your work machine set up that way.  I for one would be out of work if I tried that.

You might find that a straight VNC is the answer for you.  Personally I'm nervous about opening 5900 to the world.  VNC is anything but secure.  I even watched someone break into my Windows machine remotely (had a password on it too) when I tried it a few months ago.  Never again.  Don't know if it would have happened in Ubuntu and I'm not looking to find out.   

.

---

### Post by knightnet on 2007-05-15
If you want to use VNC or RDP remotely (e.g. over the Internet), you should most certainly be using additional security.

One very easy way to do this is to set up an SSH server on your local network and make this the only thing that can be connected to from the Internet. You can then use port forwarding under SSH to connect to the appropriate port on whatever machine you want.

There are plenty of tutorials on how to do this, it is fairly straightforwards even for newbies.

---

