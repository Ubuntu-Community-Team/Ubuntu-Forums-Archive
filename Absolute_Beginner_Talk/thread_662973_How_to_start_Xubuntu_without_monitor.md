---
title: "How to start Xubuntu without monitor?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Oceanwatcher on 2008-01-09
I have been searching Google and this forum for a solution, but the noise in the searches is so high that it is impossible to find anything. So even if I really wanted to stay out of the forum, I admit I need to ask a question or two... :) Also, since my first language is not English, it further complicates things (I am a Norwegian living in Brazil).

I have a PC with Xubuntu set up. I have Samba running fine and have been able to share some folders. So far, so good.

But I need to eventually start the box without a monitor attached. Yes, I know about the Ubuntu server version etc. , but I really need to be able to log in from the Windows PC's on the net to start and stop some programs on the Xubuntu box. So I need the GUI. Will probably end up using VNC if nobody have any better ideas.

What do I have to do to stop X from halting with an error message? Is it as simple as setting a fixed resolution or are there any other switches that need to be set?

I will ask the other questions in separate threads so they will be easier to answer and find later.

Thank you for taking the time to read this.

---

### Post by Bagster on 2008-01-09
Hi, 

I am a little confused as to exactly what you want. Firstly, do you have two seperate questions here? As I read it your problems are

 1) How do I access my ubuntu computer remotely?

2) X Fails with an error message - how do I fix this?

To answer these clearly a bit more info is needed,


1) You say you wish to access the computer from a windows box, and you say you need to a gui to start and stop some programs. Firstly, why do you need the GUI? Programs can generally be started and stopped from the command line, with no need for a GUI. For command line access you can just use ssh. Look at [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto) for more details.

If you want to run graphical programs on a windows pc from your linux box over the network, you will have to install a X server such as Cygwin on the windows pc. See [http://x.cygwin.com](http://x.cygwin.com) for details.


VNC will port the entire Ubuntu screen to your windows computer, allowing you to access it as though you are actually on it directly., I reckon though that this is overkill for what you want to do.

If you can give a bit more information about what exactly you are using the computer for and why you wish to access it remotely it would be easier to help!

2) You say you are getting an error message - what exactly are you getting? I would reccommend starting a new thread for this as it is a separate problem :)

---

### Post by Oceanwatcher on 2008-01-09
The remote access is kinda covered already. I am going to use VNC unless anyone has a better suggestion. We are 3 people that need to have simultaneous access to the box. But as I said, this one I think of as covered. I am used to use VNC and I think it is exactly what I need. As far as I understand, when you use VNC, you get new sessions, so 3 people would get 3 different sessions? I have no need for VNC over SSH. Just a plain, local connection. 

And yes. I need the GUI. Unless you would like to try to teach my wife to hack the commandline :lolflag: Seriously - this one just has to be there.

So the only thing that remains is to avoid X from stopping the boot with an error when no monitor is attached. This is my only problem. If you want to know what error it is, just pull the monitor cable out while the box is starting, then connect it after a while. There is an error onscreen. It has something to do with X not beeing able to detect the monitor resolution if I am not totally wrong. Pretty normal as there was no monitor connected.... :)

The normal situation would be that the computer complain about missing keyboard. This one don't. A keyboard is easy to stick on a hide with the pc. A monitor takes a lot more space.

This will be a small server that I am going to hide and do not want to have any other connection than ethernet. So I need to find a way to get rid of the monitor while keeping the GUI.

---

### Post by Oceanwatcher on 2008-01-19
The solution is as easy as this:

After logging in, go to the monitor settings and choose one of the monitorsettings manually. Do not select PnP. Save the setting and you are done.

I installed Webmin ([www.webmin.com](www.webmin.com)) as well and the server is running fine :-)

---

### Post by glaurens on 2008-01-24
Found the solution:

just add the line

Option "ConnectedMonitor" "CRT,CRT"


under the relative device section. Obviously if you are only running one monitor per GPU then use only one CRT.

Now I'm off to go and play with the different modes since it boots up with the incorrect resolution now, but at least it works.

The link where I found this is:

[http://gentoo-wiki.com/HOWTO_Dual_Mo...fter_X_startup](http://gentoo-wiki.com/HOWTO_Dual_Mo...fter_X_startup)

G

---

### Post by azhamjp on 2008-01-24
hello. i'm not sure if this would solve your problem. I have a headless server too. installed xubuntu because i want to keep the desktop apps to the minimum and then i disabled X server at startup. other servers (smb, ssh, ...etc) can start without the X server. 

i think you wont get errors if u dont start the X server. by the way, you don't have to hide keyboard because you propably can disable the keyboard error from the motherboard bios settings.

If u need to launch GUI apps you can start vncserver using SSH. at least that's how i get around the problem. anybody with a better solution please share.

---

### Post by neo214 on 2008-02-02
I think what he's asking here (and this is my problem) I plug it into this monitor (in my room) configure it and everything, but when I turn the headless server off (xubuntu here too) it doesn't connect to VNC server, I'm in on putty but no gui. So I have to configure it every time I want to remotely access it, kind of defeats the point.

How can you have this thing startup without a monitor and be ready to go into VNC without it giving you X errors preventing you from accessing via VNC

---

