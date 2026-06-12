---
title: "Finding Slimserver"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Pumpkin Eater on 2007-03-04
Hello all!  I've been messing around with Ubuntu for a few weeks now running a dual boot with XP until I have found apps to cover all my needs in Ubuntu.  

I have just tried to install Slimserver to run my Squeezebox from Ubuntu using the Synaptic Package Manager (multiverse and universe enabled).  It has downloaded a large number of libraries and installed various html and other files to /usr/share/slimserver.  However, no menu item or icon has been installed and I cannot find the relevant file or binary required to run the server.  In Win2k it runs in a browser window.  

Can anyone point me in the right direction?

I'm running 64 bit Edgy on a Dell Inspiron 1501 with 2 processors  and 512Mb memory.

---

### Post by pveith on 2007-03-04
Just point your firefox at "localhost:9000" that is the default port slimserver listens to.

If mothing appears there should be a "slimserver.conf" in the "/etc/"-folder and a start-script in "/etc/init.d".
so try the following:
1. open a terminal
2. type in "sudo /etc/init.d/slimserver restart"
3. enter Password
4.a Try again to access localhost:9000, if no errors were issued in the terminal
4.b post the output of the command in 2. here

Hope that helps...

---

### Post by Pumpkin Eater on 2007-03-04
Thanks pveith, that URL got the interface going.  It's still not talking to the Squeezebox but then, neither was Windoze this morning after installing a firmware update, so I think that's another issue.  :-/

---

### Post by Linux4Larry on 2007-03-05
I have a dumb question here. I too had trouble locating an icon or much evidence of slimserver on my xubuntu installation. I am able to stream from localhost:9000. I deduce that the ability to stream audio from the net means slimserver is working. 

My question is this, how do I rip a CD and then stream that/those ripped file(s) through slimserver? Xubuntu ships with xgine, but that seems to only want to rip a CD back onto another CD. I want to rip onto my harddrive. Can I just copy the music files? Is there a light weight/small footprint ripper that I can download onto xubuntu?

My computer is a 500MHz CPU, 384MB RAM and 20 Gig  HD. For some reason, it is really sluggish and occasionally just locks up - I've only downloaded slimserver so far, and the Windows 98 install had similar problems. 

Thanks, 
Larry

---

### Post by wieman01 on 2007-03-07
> **Linux4Larry said:**
> I have a dumb question here. I too had trouble locating an icon or much evidence of slimserver on my xubuntu installation. I am able to stream from localhost:9000. I deduce that the ability to stream audio from the net means slimserver is working. 

My question is this, how do I rip a CD and then stream that/those ripped file(s) through slimserver? Xubuntu ships with xgine, but that seems to only want to rip a CD back onto another CD. I want to rip onto my harddrive. Can I just copy the music files? Is there a light weight/small footprint ripper that I can download onto xubuntu?

My computer is a 500MHz CPU, 384MB RAM and 20 Gig  HD. For some reason, it is really sluggish and occasionally just locks up - I've only downloaded slimserver so far, and the Windows 98 install had similar problems. 

Thanks, 
Larry
There is an article in the Wiki that helps you get going with CD ripping: [https://help.ubuntu.com/community/CDRipping]("https://help.ubuntu.com/community/CDRipping")

Second, all you need to do is store those MP3 files in a folder and tell Slimserver where to find these files. Use the HTML GUI (browser) to configure Slimserver, there is an option that lets you set your favorite music folders. 

As for the icon, there is none because Slimserver is solely configured through HTTP i.e. your browser (or command line if you prefer that).

---

