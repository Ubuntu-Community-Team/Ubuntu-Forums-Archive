---
title: "Access"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Yizi on 2007-08-30
Hello,

Is it possible to access someones PC if you know the IP with Ubuntu?
If yes how we do that.

---

### Post by Steveway on 2007-08-30
You can setup an ssh server.

---

### Post by Yizi on 2007-08-30
What about if that PC is based on Windows or any other OS's then Linux?

---

### Post by Steveway on 2007-08-30
You can use putty on windows to log into your Linux.

---

### Post by Yizi on 2007-08-30
No what i ment was my friend lives in scotland, she uses Windows as OS, i was wondering if i could access her PC with Ubuntu with the IP. 
If thats possible what program we use and how?

---

### Post by Steveway on 2007-08-30
Ahhh so you want to access a windows Pc with Ubuntu.
You should have said that in your first post.
I can't help you with that, never came across such a situation.

---

### Post by Yizi on 2007-08-30
> **Steveway said:**
> Ahhh so you want to access a windows Pc with Ubuntu.
You should have said that in your first post.
I can't help you with that, never came across such a situation.

OK, anyone else?!

---

### Post by yota on 2007-08-30
You can use tsclient (terminal services client) which is installed by default (it even has an icon under applications/internet/terminal services client).
Moreover you can use also rdesktop and krdc which are available in the repositories.
All these three support the microsoft rdp (remote desktop protocol) and enable you to connect to a windows box  which has remote desktop/terminal services enabled.

Another solution could be to install a vnc server on the windows box (like ultravnc) and use a vncviewer on linux.

Hope this helps!

---

### Post by Yizi on 2007-08-30
> **yota said:**
> You can use tsclient (terminal services client) which is installed by default (it even has an icon under applications/internet/terminal services client).
Moreover you can use also rdesktop and krdc which are available in the repositories.
All these three support the microsoft rdp (remote desktop protocol) and enable you to connect to a windows box  which has remote desktop/terminal services enabled.

Another solution could be to install a vnc server on the windows box (like ultravnc) and use a vncviewer on linux.

Hope this helps!

OK, what shall i put for Domain and Client Host Name?

---

### Post by beercz on 2007-08-30
Try Gnome-RDP - it's in the repos.

Gives you a remote desktop connection to a windows pc - provided it's XP Pro or Windows Server 2003 and probably Vista too - but I haven't tried that.

Also look at using vnc as a possibility - although I believe it's not that secure.  I only use vnc on a LAN and not across the internet.

[http://www.realvnc.com/](http://www.realvnc.com/)

---

### Post by yota on 2007-08-30
> **Yizi said:**
> OK, what shall i put for Domain and Client Host Name?

Insert the ip address as the host name, fill in the user and password fields correctly, and leave empty the domain if (most likely) the pc you are connecting to is not a member of an active directory domain.

---

### Post by Yizi on 2007-08-30
> **beercz said:**
> Try Gnome-RDP - it's in the repos.

Gives you a remote desktop connection to a windows pc - provided it's XP Pro or Windows Server 2003 and probably Vista too - but I haven't tried that.

Also look at using vnc as a possibility - although I believe it's not that secure.  I only use vnc on a LAN and not across the internet.

[http://www.realvnc.com/](http://www.realvnc.com/)

Where do i get Gnome-RDP and how do i install it?
I have problem installing packages. :-s

---

### Post by Yizi on 2007-08-30
> **yota said:**
> Insert the ip address as the host name, fill in the user and password fields correctly, and leave empty the domain if (most likely) the pc you are connecting to is not a member of an active directory domain.

Thanks Alot Yota it worked perfectly! :KS

---

### Post by beercz on 2007-08-31
> **Yizi said:**
> Where do i get Gnome-RDP and how do i install it?
I have problem installing packages. :-s
Have you enabled the multi-verse and universe repositories in synaptic? (Can't remember which one gnome-rdp is in).

What problem are you having installing packages?

---

### Post by wormser on 2007-08-31
This is pretty complicated for a thread to explain because there are a lot of steps.  Check out this[ guide]("http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx") to enable Remote Desktop on XP.  It has to be XP Pro and not Home.  Home does not have this feature, but you can user [VNC]("http://www.realvnc.com/") instead.  You will also have to open up the port on the remote [router's firewall]("http://portforward.com/routers.htm").

After setting up the remote machine, on the Ubuntu box go to Applications> Internet> Terminal Server Client.  Under computer put the IP address.  Under Protocol use RDP.  If you set up a VNC server then put VNC.  Click connect.

---

### Post by wieman01 on 2007-08-31
I also second that. Installing a **VNC** server on the remote (Windows) PC is the easiest option.

And try something called "Dyn DNS". It lets you access another PC using a fixed name rather than an IP that keeps changing.

---

### Post by Yizi on 2007-08-31
Thanks a lot everyone i will give a try again and let you know what happened. ;)

---

