---
title: "advice needed on how to bypass blocked ports behind a proxy to access Gmail"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2008-04-10
Ok, I was not sure where to post this so I thought I would start here (mods: please feel free to place it in an approprite Forum).

i am behind a work proxy that has blocked certain ports, and looks like it has captured the ports Gmail imap/smpt SSL port along with that. so I can't dowload my email in evolution. Have to access Gmail via web-access.

I am not sure if there is a way to bypass the blocked ports in Ubuntu? any clever (but legal) hacks that I could try so I am back using Evloultion for my mailing/calendering needs.
I did some searching, and MacOSX has a tool called [proxytunnel]("http://www.macosxhints.com/article.php?story=20050804072524306&mode=print"), ii did not understand the process that well. If anyone could help me out and get be to access Gmail through Evolution and the blocked ports, I would really appreciate it.

Best,
S

---

### Post by jw5801 on 2008-04-10
That's actually quite a neat little system! They set up a global ssh server that you can connect to through a common port (one that won't be blocked on your proxy) and from there forward whatever port you'd like back through to your home machine.
proxytunnel is Unix based (hence the OSX hint), so it's also available for Linux. I'll give it a try and see what happens. Won't have an opportunity to test it until next week sometime though. I'll report back!

---

### Post by jw5801 on 2008-04-10
Ok, well it's easy enough to install! Get the source from [here](http://sourceforge.net/project/showfiles.php?group_id=39840&package_id=32673&release_id=581514).
Then you'll need the build-essential and libxmlsec1-dev packages installed. Then make and sudo make install, and you should be able to use the commands on the page you linked. Or to summarise:
```
wget http://downloads.sourceforge.net/proxytunnel/proxytunnel-1.9.0.tgz
sudo aptitude install build-essential libxmlsec1-dev
tar xvf proxytunnel-1.9.0.tgz
cd proxytunnel-1.9.0/
make
sudo make install
```

Unfortuneately I can't test it until Monday, so if you have the opportunity, go for it and report back. If it works properly I may even write up a how-to for it.

---

### Post by brian_p on 2008-04-10
> **shuttleworthwannabe said:**
> Ok, I was not sure where to post this so I thought I would start here (mods: please feel free to place it in an approprite Forum).

i am behind a work proxy that has blocked certain ports, and looks like it has captured the ports Gmail imap/smpt SSL port along with that. so I can't dowload my email in evolution. Have to access Gmail via web-access.

I am not sure if there is a way to bypass the blocked ports in Ubuntu? any clever (but legal) hacks that I could try so I am back using Evloultion for my mailing/calendering needs.
I did some searching, and MacOSX has a tool called [proxytunnel]("http://www.macosxhints.com/article.php?story=20050804072524306&mode=print"), ii did not understand the process that well. If anyone could help me out and get be to access Gmail through Evolution and the blocked ports, I would really appreciate it.

Best,
S

Asking your system administrator to facilitate downloading mail from gmail would seem to be quicker and less stressful than compiling some software which may or may not work.

---

### Post by shuttleworthwannabe on 2008-04-10
Hey, thanks a million. I will rather wait for your HOWTO. I may give it a try as well as soon as I get off work. Will check back to see what your experience was.

---

### Post by shuttleworthwannabe on 2008-04-10
I tried with system admin: no joy, as it is corporate policy. Beat that.

---

### Post by brian_p on 2008-04-10
> **shuttleworthwannabe said:**
> I tried with system admin: no joy, as it is corporate policy. Beat that.

So you would have to be careful not to offset any technical success by having to look for another job.

---

### Post by BobbyIceCubes on 2008-04-10
Unfortunately it is probably not the ports that are blocked. It is usually blocked by Proxy Policy. Depending on how good your Proxy team is, their would be no way around it. I have user access groups that associate with the users authentication credentials, which would enable access to webmail. Unless you are part of this specific access group, the on box content filter will block webmail of any type, especially if your place is using a content filter such as Websense, or Bluecoat content filtering. I am a certified Bluecoat Proxy Engineer by trade. If Gmail is being blocked by port, then you might be able to work your way around it (but if they are as good as my team I doubt it  ;-)  )

---

### Post by anagor on 2008-04-10
To answer the original question:
If you have an external, under your control machine, let's say your home PC, which is stays connected to the net, you can use ssh as a socks proxy.
You will have to do some tweaking and install additional packages but it's quite easy I believe.
Here is a working example:
On my home PC I have installed ssh meta-package, which includes openssh-client and openssh-server.
$sudo apt-get install ssh

The sshd daemon will start automatically the next time you reboot, but to run it manually you can issue:
$sudo /etc/init.d/ssh start

Now, my PC is behind a router, so on my Router I've forwarded the 443 port from outside to a 22 port on my PC. (443 is used for https therefore it is open on most if not all corporations' firewalls)

If your PC is connected directly to the Internet, first of all I suggest to use firewall, if you aren't using one already, secondly, you will have to change the default port that ssh daemon is listens on:
open the /etc/ssh/sshd_config file as root and look for the line that states:
Port 22
usually it's the first non-commented line.
change the Port to 443, and restart the ssh daemon:
$sudo /etc/init.d/ssh restart

This is the home PC configuration, now to the laptop at work.
you will need openssh-client package and tsocks package, the tsocks needed since evolution doesn't use proxy at all, so:
$sudo apt-get install openssh-client tsocks

Now, go to tsocks config file, it's path is: /etc/tsocks.conf, open it with your preferred text editor as root and go to the end of the file, look for the line:
server = 
change the IP that is there to 127.0.0.1

Now, open an ssh connection from your laptop to your home PC, of course for that you will have to know the external IP of your home PC, let's say it's 123.231.123.231
you will do it like this:
$ssh -D 127.0.0.1:1080 <user>@123.231.123.231

replace the <user> with the user name on your home PC.
ssh client will ask you for password, supply it to him, (your home password of course :) )
You will see a prompt of your's home PC shell, btw this is a working shell on your home PC, so please use strong passwords. As long as this terminal window remains open, you have a socks proxy server running on your laptop on 127.0.0.1 port 1080, this is the -D command for.

Now open another terminal and execute:
$tsocks evolution

This will open up an evolution client, that now uses the socks proxy for it's communication.

It's maybe looks like a lot of work, but you need to do it only once, from there on all you have to do is:
in first terminal to run the ssh client: $ssh -D 127.0.0.1 <user>@123.231.123.231
and in the second terminal to run: tsocks evolution

It's what I do to bypass my work's firewall.

---

