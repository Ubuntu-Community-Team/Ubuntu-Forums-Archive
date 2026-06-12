---
title: "Using HOSTS to block unwanteds"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by angler on 2006-10-15
Hey, first post here, so hello all. New to Ubuntu and really liking it so far, plan to stick with it and make the big switch. Anyway, to the point...

I have adblock for mozilla which is pretty much the same as my adshield for internet explorer, but I would like to block more ads and otherwise bad IPs by using the HOSTS file in the same way I have done in windoze. I know both systems use the hosts file and i think the 127.0.0.1 redirect should work the same either way, but when I re-authored the HOSTS file in ubuntu, I was totally locked out of the system. It could no longer recognize my user name and 'sudo" commands all gave an error that I can't remember right off, but something like 'unable to find "user" by <getuser> - just to give the idea.
Anyway, if anyone has tried this or has suggestions I would love to here them. Please keep in mind, I'm a ubu noob. bryan, va

---

### Post by Kateikyoushi on 2006-10-15
I want to try it as well, already got a few hosts file but did not edit them yet. I am curious what went wrong. I checked but not much info about it on the forum so far.

---

### Post by John.Michael.Kane on 2006-10-15
[http://ubuntuforums.org/showthread.php?t=241460&highlight=block+site](http://ubuntuforums.org/showthread.php?t=241460&highlight=block+site)

Heres a site that has host files [http://hostsfile.mine.nu/](http://hostsfile.mine.nu/)

---

### Post by Kateikyoushi on 2006-10-15
Thanks for the guide insteresting that I also did a search and did not come up.
Seems only have to add the current 1-2 lines to the block list and replace the old one.
Makes me wonder where did angler go wrong.

---

### Post by angler on 2006-10-15
yeah, I read something about it being simple as that... so I copied the few lines of text from the native HOSTS file on to the top of my block list HOSTS file and created a backup of the originial called HOSTS_BACKUP. Well, that was it. I was no longer recognized as a user and as a result sudo commands wouldn't give me rights to go back and replace the file with the _BACKUP version. I had only installed Ubuntu a few hours earlier and wanted to solve some other issues anyway, so I reinstalled fresh. I would be very cautious trying this out, maybe there is a way to do it for a limited account and see how it does? Otherwise, I think there is a DNSkong thing I can try to use.
Thanks all....

---

### Post by angler on 2006-10-15
Ok, so I ran the script posted by bodhi.zazen and I don't see any change to my HOSTS file at all. Am I missing something here? The script seemed to run perfectly and I expected to see a bunch of 127's in the HOSTS but it looks to be unchanged?? I'm going to reboot and make sure things are still good, but I really appreciate the response. I'll do some more searching on the subject and post what I find. Sorry for being such a nUb.

---

### Post by fragos on 2006-10-16
There should be a line in your /etc/hosts file like:

127.0.0.1 localhost Geo

In this example "Geo" is the name in /etc/hostname.  If the two don't jive you will be locked out of administrative tasks.

---

### Post by CatKiller on 2006-10-16
What fragos said. The /etc/hosts file isn't **just** used for blocking ads, you know. Leave the stuff at the top of your file and put your adserver redirects at the bottom. Otherwise, you'll break it.

---

