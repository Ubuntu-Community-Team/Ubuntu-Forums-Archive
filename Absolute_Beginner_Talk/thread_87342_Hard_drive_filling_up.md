---
title: "Hard drive filling up"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by Ahriman on 2005-11-07
I have my Ubuntu hard drive partitioned like this:

/        10GB
swap   1.5GB
/home  28.5GB

I went (as I'm sure alot of people do) on an installing spree through synaptic. Now, though, performance is very laggy, and last night when I tried logging in, I got an error saying that I couldn't log into the X server environment because there wasnt enough space.

I worked out from the message that it was the / partition that was out of space, and after deleting some files in the /var/www directory, I was able to log back in. gParted shows an available 600MB on this partition.

Is there a way that:

a) I can tell synaptic to install programs to my home directory (ie. /home/ahriman/progs)?; or
b) I can see what is safe to delete on the / partition (ie. log files, cached packages, etc)

I have uninstalled what I don't use anymore via synaptic, but the most I have managed to clear is 1.2GB. If someone could give me an idea of what to do, I would be most grateful.

Cheers! :)

---

### Post by Xian on 2005-11-07
Well, if you have any free space on the HD it would probably be wise to make another partition for a directory like /usr and then just move it over to that location. In that way you would effectively increase the capacity of / without having to resize anything.

If not, you will still need to find where most of your space is being used. There is a nice GUI tool called filelight that can do this, or you can just use the command below in a terminal.

```
$ sudo du -sh /*
```

---

### Post by Ahriman on 2005-11-07
[QUOTE=Xian]```
$ sudo du -sh /*
```[/QUOTE]
I ran this, and it showed that my /var directory was 5.7G

so I went into it, and ran: sudo du -sh /var/*

and it showed that the /var/log/ directory was 5.5GB

Can I delete everything in this directory? Is it just log files, or is there anything important in it?

Will be attempting to put /usr on another drive, too, it rang up at only 2G, but I'm tyring to think ahead :)

---

### Post by Xian on 2005-11-07
[QUOTE=Ahriman]it showed that the /var/log/ directory was 5.5GB

Can I delete everything in this directory? Is it just log files, or is there anything important in it?[/quote]
Nothing in the /log directory is system critical.
However, why not narrow the search some more?

You will want to find out the source of the problem.
In this way you might be able to avoid re-creating this issue.

Here is an example of my own system:

```
# sudo du -h /var/log
4.0K    /var/log/news
4.1M    /var/log/installer/cdebconf
4.7M    /var/log/installer
28K     /var/log/cups
24K     /var/log/gdm
8.4M    /var/log
```

[QUOTE=Ahriman]Will be attempting to put /usr on another drive, too, it rang up at only 2G, but I'm tyring to think ahead :)[/QUOTE]
2G is significant on a 10G partition. The idea is to consider moving your largest directory(s) to a separate partition to assist with space issues in your root path. However, it would seem the /var/log is your most pressing matter.

---

### Post by souki on 2005-11-07
Unless you need some informations from the log files, you can empty them:
```
true > /var/log/message
```
if you want to know which ones are big:
```
ls -lrS /var/log/
```
If your system is a simple desktop, it's not usual to have so much logs. It might be usufull to look at the end of the biggest log-file:
```
tail -n50 /var/log/the-big-file.log
```

---

### Post by poptones on 2005-11-07
Blah. My bet is your synaptic cache is clogged with all those packages. If you are on broadband and won't be needing the packages again just remove all those debs and you'll probly free up half a gig or more.

sudo rm /var/cache/apt/archives/*deb

I'm on dialup so I keep these stored elsewhere and when I reload I link them back. My cache is something like a GB now and all I've added to the base install is build tools, header files, and a new kernel. check yours and see what's in there...

BTW, 5GB for a lo directory is effin huge. Something might be up there as well.

---

### Post by Ahriman on 2005-11-07
when I run: sudo du -sh /var/log I get the following:
```

5.5G    /var/log

```

I ran: ls -lrS /var/log/  and the bottom three are listed like so:

```
-rw-r-----  1 root  adm  1948326762 2005-11-08 07:07 kern.log.0
-rw-r-----  1 root  adm  1948333811 2005-11-08 07:07 messages.0
-rw-r-----  1 root  adm  1948356225 2005-11-08 07:07 syslog.0

```
The other files listed were all 1.7mb or lower.

As I am running a simple desktop, is it safe to delete these files? I looked in them (using your command *tail -n50 /var/log/the-big-file.log*, and all I see is system messages that mean nothing to me.
Also, is there a script I can install to clear log files from here periodically?
Edit: I looked in the /var/cache/apt/archives/ directory, and there were only a few files in there (around 8 or so, other than the lock and partial directories). I deleted them, anyway, but it didn't get rid of much space. Thanks anyway, I now know how to clear those files out (which I was going to ask about once this got sorted out :))

---

### Post by souki on 2005-11-07
well, your log files are too big :)

you can do:
```
true > /var/log/kern.log.0
true > /var/log/messages.0
true > /var/log/syslog.0
```

these files are rotated and compressed daily or weekly. I don't know where this is done on ubuntu, but you have enough room on your partition to run ubuntu

but your logs are too big for a normal desktop usage, you have to fix this.
do you have a lot of repeating messages in it? I suppose you have some warnings from the kernel, for example, this is what I have:
```
[4299001.623000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299001.623000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

please, try with "tail" as in the previous post, and try to detect duplicates messages

---

### Post by Ahriman on 2005-11-08
I have posted onto a friend's website the output from the tail command (thought they might be too much for the forums)
[kern.log.extract.txt]("http://localghost.wiredguides.com/files/kern.log.extract.txt")
[messages.extract.txt]("http://localghost.wiredguides.com/files/messages.extract.txt")
[syslog.extract.txt]("http://localghost.wiredguides.com/files/syslog.extract.txt")

If, as you say, they get rotated every week or so, then this probably won't be the case, but I was wondering if it could be due to me upgrading from Hoary, and not reformatting and doing a clean install.

---

### Post by gruepig on 2005-11-08
I don't think upgrading should have had made your logs that big.  You can probably just delete the large log files (or preferably 'echo true' as suggested).  Check the size of your log files again in a few days, but maybe this is a one-time thing.

If you're curious about log rotation, you can look at -- or modify -- the configuration in /etc/logrotate.conf and the files in the /etc/logrotate.d/ directory.

And though cached .deb files (/var/cache/....) does not appear to have been the culprit, you can purge the cache regularly by executing the command 'sudo apt-get clean'.  (I put this in cron so it runs automatically; e.g., edit /etc/crontab and add the line '0 6 * * 7 root /usr/bin/apt-get clean').

---

### Post by Ahriman on 2005-11-08
Thanks to all for all the help. I really appreciate everything. This is one of the reasons that brought me to Ubuntu: the community.

a thousand blessings

---

