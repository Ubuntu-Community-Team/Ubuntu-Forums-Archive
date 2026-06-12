---
title: "[SOLVED] Firefox Problem Freezing - How do I install tar file from Mozilla"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-17
Ok I've been having probs with firefox freezing for 15 seconds and the cpu goes to 100%.

Someone suggested that the mozilla version was better than the repo version for some reason.

Anyway I downloaded the tar file extracted to my desktop had a look in the folder and there are all the relevant files. Just like extracting a zip file.

Now how to I install it without cocking up synaptic do I just extract it into /usr/lib with another name for the folder like firefoxmoz. That way I keep synaptic happy?

---

### Post by Kilz on 2007-08-17
> **philinux said:**
> Ok I've been having probs with firefox freezing for 15 seconds and the cpu goes to 100%.

Someone suggested that the mozilla version was better than the repo version for some reason.

Anyway I downloaded the tar file extracted to my desktop had a look in the folder and there are all the relevant files. Just like extracting a zip file.

Now how to I install it without cocking up synaptic do I just extract it into /usr/lib with another name for the folder like firefoxmoz. That way I keep synaptic happy?

I like the /usr/local/ directory for applications I install. But its up to you. You could also try another mozilla build like [Swiftweasel]("http://sourceforge.net/projects/swiftweasel/"). It even has deb files.

---

### Post by philinux on 2007-08-17
So your saying all I need to do is extract it basically anywhere but run it by pointing a launcher at my version of firefox that way it keeps synaptic happy.

By the way I went into the firefox folder on my desktop clicked on the firefox executable and hey presto it picked up my profile etc.

I believe its bad news to uninstall the ubuntu version. Will there be any conflict with updates?

---

### Post by steve.horsley on 2007-08-17
I use the real Firefox from Mozilla. I unzip the tar to /opt (it's shorter to type than /usr/local). Then I put a symlink to /opt/firefox/firefox in the /usr/local/bin directory. This directory is earlier in the path than /usr/bin, so my firefox becomes the preferred one.

---

### Post by philinux on 2007-08-17
Thanks for reply, did you have problems with firefox freezing and using 100% cpu

Whats a symlink

---

### Post by philinux on 2007-08-18
Bump

Anyone?

---

### Post by steve.horsley on 2007-08-18
No I didn't have trouble with iet actually freezing, but sometimes took half a minute to make a real mess of some of our intranet pages when the real FF from Mozilla drew them perfectly in a fraction of a second.

A symlink is a symbolic link to another file in another place. I put the symbolic link in /usr/local/bin and the OS behaves as though the file is there, but uses the link target (/opt/firefox/firefox) instead. My link looks like this:
> steve@StevesPC:~$ ls -l /usr/local/bin/firefox 
lrwxrwxrwx 1 root root 20 2007-06-17 14:00 /usr/local/bin/firefox -> /opt/firefox/firefox

and I made it with this command. ln -s means link symbolic:
**sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox**

---

### Post by kerry_s on 2007-08-18
> **philinux said:**
> Ok I've been having probs with firefox freezing for 15 seconds and the cpu goes to 100%.

Someone suggested that the mozilla version was better than the repo version for some reason.

Anyway I downloaded the tar file extracted to my desktop had a look in the folder and there are all the relevant files. Just like extracting a zip file.

Now how to I install it without cocking up synaptic do I just extract it into /usr/lib with another name for the folder like firefoxmoz. That way I keep synaptic happy?

Yes that will work.

```
sudo rm -rf /usr/lib/firefox
sudo cp /path/to/new/firefox /usr/lib/firefox
sudo rm -rf /usr/lib/firefox/plugins
sudo ln -s /usr/lib/mozilla-firefox/plugins /usr/lib/firefox/plugins
sudo rm /usr/bin/firefox
sudo ln -s /usr/lib/firefox/firefox /usr/bin/firefox

```
hope that's simple enough for you to understand.

i see your running a low tech system like mine(450mhz 256ram), i found the secret is to use the DSL version of firefox(1.0.6) they built it for performance, it's not as pretty & extentions are less, but it's fast & never freezes, yet still gives you a full browser for sites that need it. dillo is my main browser. so if you want to try that grab a DSL live cd, boot it up & copy there firefox folder to your drive or usb pen & install it the same as your doing now.

---

### Post by philinux on 2007-08-18
Found a simpler solution after a bit of poking about.

Followed the instructions here
[http://ubuntuzilla.wiki.sourceforge.net](http://ubuntuzilla.wiki.sourceforge.net)

Now I've got the mozilla version of firefox and it don't freeze at least on my rig. And I've got thunderbird 2 which also now has webmail/hotmail. Both update as soon as mozilla release an update.

Excellent solution.

---

