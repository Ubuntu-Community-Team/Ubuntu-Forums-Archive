---
title: "networking problems -- loopback?"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2006-03-03
Hi:

I am on this computer which is running Breezy. I have another Linux computer, Fedora FC4, on which I run the SlimServer music software ([www.slimdevices.com)](www.slimdevices.com)). You connect to it via a Web browser and all my other computers connect to it fine... except for this fine Ubuntu one. And I think it's because I messed around with the settings under "System>administration>networking>hosts" when I was setting up this comp as a Samba server. 

When I open FireFox and type in the URL of the SlimServer software ([http://localhost:9000/stream.mp3](http://localhost:9000/stream.mp3)) I am forwarded to this URL [http://blade.nagaokaut.ac.jp/cgi-bin/scat.rb/ruby/ruby-talk/129658](http://blade.nagaokaut.ac.jp/cgi-bin/scat.rb/ruby/ruby-talk/129658) .... don't ask me why. Or how.

Does anyone know the default settings for the series of boxes listed under 'hosts'? Or do you have a better idea? Thanks.

GM

---

### Post by Sandlst on 2006-03-03
I don't have a better idea-although there probably is one-Ill post my Hosts, as if you were entering them all for the first time:

IP address: ff00::0
Aliases: ip6-mcastprefix

IP address: 127.0.0.1
Aliases: localhost.localdomain
           localhost
           [COLOR="Red"]node-729[/COLOR]

IP address: fe00::0
Aliases: ip6-localnet

IP address: ff02::2
Aliases: ip6-allrouters

IP address: ff02::1
Aliases: ip6-allnodes

IP address: ::1
Aliases: ip6-localhost
           ip6-loopback

IP address: ff02::3
Aliases: ip6-allhosts

my computer's name is [COLOR="Red"]node-729[/COLOR], so you will want to replace that

---

### Post by GMachine_24 on 2006-03-04
Thanks for your reply. The error turned out to be in the 'hosts' section:

IP address: 127.0.0.1
Aliases: localhost.localdomain
localhost

I had to change the IP address to the actual IP address of the server and change "localhost" to the actual host name of the server. Other than that everything is swell.

Thanks!!

GM

---

### Post by GMachine_24 on 2006-03-04
Hi:

As you can see from the posts above I thought I had this problem solved. However, no.

Once again:

I am typing this post on a Breezy Linux machine. The computer with SlimServer installed is a Fedora FC4 machine. All my computers, except this Breezy box, connect to SlimServer via a Web browser and play music without a problem using SoftSqueeze software (or sometimes Winamp - all the clients save this one are Windows XP machines).

However, when I open a browser window on this (Breezy) machine and type in

[http://localhost:9000](http://localhost:9000)

(where 'localhost' is the actual name of the local host on the FC4 box)

I am immediately forwarded to this URL: [http://blade.nagaokaut.ac.jp/cgi-bin/scat.rb/ruby/ruby-talk/129658](http://blade.nagaokaut.ac.jp/cgi-bin/scat.rb/ruby/ruby-talk/129658)

which makes no sense to me but that's what happens.

The only thing I can think of is my first name is "Erik" and if you look at the blade.nagaokaut.xxxxxx Web page from the link above you will notice and email and domain with "erik" in them. That is the only thing I can figure out.

I have tried various "host" settings on the Ubuntu networking configuration GUI - sometimes I can get the browser to open the SlimServer GUI by changing the "hosts" setting under "networking" (System>Administration> -- changing the setting for the line that has the 127.0.0.1 IP address - I change the IP address to that of the SlimServer box, and I change the localhost and localhost.localdomain to match those of the SlimServer computer. Then I can pull up the SlimServer GUI via the FireFox browser but when I attempt to play music using the XMMS player by typing in the URL [http://localhost:9000/stream.mp3](http://localhost:9000/stream.mp3) into XMMS ("add url"), XMMS freezes and eventually I have to reboot the computer (how like Windows).

If anyone has any idea how/why this happens and what I can do to correct it, please let me know.

For the record, all my computers show up on my local network and all can be accessed by the others - with this one exception.

If it matters, both the Fedora FC 4 with SlimServer and this Ubuntu Breezy machine have Samba installed and working.

Thanks.

GM

---

### Post by GMachine_24 on 2006-03-04
Ok people, if anyone is reading this do NOT waste your time attempting to assign values to the 'hosts' setting under network configuration. I spent hours today attempting everything I could thing of, with no positive results.

So, in the end, I did the smart thing. I stopped beating my head against the wall, did a 'netstat' and figured I might just be able to access SlimServer from this Ubuntu machine if I just typed in the IP address + its extension (in this case :9000). 

It works every time.

So, you open Firefox (or Mozilla, whatever) and type in

[http://192.168.0.102:9000](http://192.168.0.102:9000)

(in my case - other people might have a different IP address, e.g. 192.168.0.103, but the :9000 extension will remain the same).

Hit enter, and you get the SlimServer GUI.

Now, I have still not figured out how to get XMMS to play the music stream coming from SlimServer - XMMS freezes at every attempt. I downloaded the SoftSqueeze software GUI from [www.slimdevices.com](www.slimdevices.com) (use the .zip file, don't attempt to convert the rpm to a deb using alien as you will end up with a file you cannot use) and then follow the directions for starting SoftSqueeze from the command line (all of this can be found here 

[http://softsqueeze.sourceforge.net/download.html](http://softsqueeze.sourceforge.net/download.html)

I get an error message every time I run SoftSqueeze that it cannot connect to the SlimServer and that I should check my network settings - which are correct except I haven't figured out how to enter the version of SlimServer (6.2.1) I am using into the SoftSqueeze interface. I don't know if that will do the trick or not. If I find out, I will post the answer here.

GM

---

### Post by scohar70 on 2007-05-26
> I downloaded the SoftSqueeze software GUI from [www.slimdevices.com](www.slimdevices.com) (use the .zip file, don't attempt to convert the rpm to a deb using alien as you will end up with a file you cannot use) and then follow the directions for starting SoftSqueeze from the command line (all of this can be found here

[http://softsqueeze.sourceforge.net/download.html](http://softsqueeze.sourceforge.net/download.html)

Thanks for this.  I was finally able to get SoftSqueeze working on Fiesty.  I created a little startup script because I'm too lazy to remember the java command:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# Performs a backup of my files
echo "Starting Softsqueeze..."
cd ~/bin/softsqueeze-dir
java -jar SoftSqueeze.jar &
```

---

