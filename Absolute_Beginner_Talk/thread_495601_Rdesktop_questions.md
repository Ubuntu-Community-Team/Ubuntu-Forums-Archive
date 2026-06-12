---
title: "Rdesktop questions"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-07-08
Hello,

Can I use rdesktop to run windows seamlessly within Ubuntu, when my Ubuntu and Windows partitions are on the same disk?

I already installed VMWare Player to run Windows in its virtual environment. I also installed VMTools and Seamlessrdp in Windows and rdesktop in Ubuntu.

Now I'm stuck because I don't know what to look for to make the connection between the two partitions work. HELP!

Also, I installed NTFS-3G to access and modify the windows partition files, but although I can visualize the files, I can't modify them at all or even create new ones there. How is that???

Thanks!

---

### Post by the8thstar on 2007-07-08
Help please!

---

### Post by hysteresis on 2007-07-08
I don't think this is possible. remote desktop is used to connect a client to a server. Besides, windows has to be running on the machine you connect to.

---

### Post by iver2435 on 2007-07-11
It is possible to set up, I have my system set up this way, however I do agree with hyster that Windows needs to be actually running inside a VM for this to work.

Here's what I did to set up my system this way.....

I installed the vmware-server package from the repos.....word of caution, if you are going to try to install vmware-server in place of vmware-player (as I did) you have to first remove the vmware-player package and then remove the /etc/vmware directory, otherwise the install script for vmware-server will get all messed up.

So, once you have your vmware-server set up, open the console, input your VM settings and install Windows into a VM.  Make sure you choose NAT networking as an option when it comes up, and for everything else just pick what makes sense.

Once the VM is up and working, make a note of the IP address of the VM machine ("ipconfig" in a terminal).

Inside the Windows VM, download [SeamlessRDP]("http://www.cendio.se/files/thinlinc/seamlessrdp/seamlessrdp.zip") and extract it to C:\seamlessrdp.

Now you should be ready to actually USE your VM for it's intended purpose. Open a terminal windows and type in this command:

```
rdesktop -A -P -N -k en-us -u <username> -p <password> -s "c:\seamlessrdp\seamlessrdpshell.exe c:\Program Files (x86)\Internet Explorer\iexplore.exe" -5 -r sound:local <IPAddress>

```

if you want to know what all the options are, just do a "rdesktop -?" and read about them.  This command is the actual command I use to run Internet Explorer on my desktop.  Two things.....first, I'm running WinXP 64bit in my VM, so my path to IE is different than if I was running 32 bit.  Please adjust yours accordingly.

Second, where you see <username>, <password> and <IPAddress>, replace those with the username and password of the Windows user you're going to run the program under and the IP Address of the VM you noted earlier, respectively.

I got my information for doing all this in a very nice guide posted [Here]("http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/")

Hope I made sense during all of this...  lol

---

### Post by Ansible on 2007-07-28
I've been using seamlessrdp in this way the past week or so.  Very cool.  Normally I run internet explorer as in your sample command, and then navigate to whatever program I want to run from there.  I've had it happen that I've closed the IE window, then I try to bring up explorer again from another application's Open dialog, by right clicking on a folder and selecting Explore.  This brings up the whole windows desktop on one of my workspaces, with the start bar and everything.  After that, every time I run my seamless rdp script, I get the full workspace again and not just the IE window.  The only way to fix it seems to be a reboot.  Have you encountered this problem, and found a solution?  

Also, I saw a demo of seamlessrdp where someone had a control on their ubuntu gnome panel that had all the windows start menu items on it.  Apparently you could start whatever program you wanted from that - what program is this?

---

### Post by the8thstar on 2007-12-15
Bump

---

