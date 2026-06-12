---
title: "thunderbird"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Andrew79 on 2008-03-27
Hi Ya'll,
 can someone tell me in a simple way how to download thunderbird and install it? I can get to the site, I download, then I am lost of what to do to make it install.....
Thanks

---

### Post by dragonflyFZX on 2008-03-27
in a terminal program, type
sudo apt-get install thunderbird
then type your root password

I just did this to install thunderbird

---

### Post by lawentzel on 2008-03-27
Or, if you would like an easier way, click on "Applications, Add/Remove" and search for Thunderbird.  It's in there.

---

### Post by stchman on 2008-03-27
> **Andrew79 said:**
> Hi Ya'll,
 can someone tell me in a simple way how to download thunderbird and install it? I can get to the site, I download, then I am lost of what to do to make it install.....
Thanks

Gutsy has the latest Thunderbird in it's repositories.

```
sudo apt-get install thunderbird
```

---

### Post by ajgreeny on 2008-03-27
As the previous three posters have said use apt-get or synaptic or add-remove to do this sort of thing.  You are using linux now so forget all that you learned using windows and go with the flow, the apt-get or synaptic flow.

Seriously, you need to forget how you did things in windows (I assume you are coming from that OS use) and use the fabulous tools at your disposal in Ubuntu for installing just about anything, synaptic, apt-get and Add-Remove.  When you are a bit better aquainted with the system you can try to download and install tar-balls if you really want to, but it is not honestly ever necessary using Ubuntu.

---

### Post by Andrew79 on 2008-03-27
andrew@andrew-laptop:~$ sudo apt-get install thunderbird
[sudo] password for andrew:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package thunderbird has no installation candidate
andrew@andrew-laptop:~$ sudo apt-get install thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package thunderbird has no installation candidate


Okay, this is what I got. i also tried add/remove and it says it downloaded it, but where did it go???

---

### Post by lawentzel on 2008-03-27
Silly question, but did you look in Applications, Internet?

---

### Post by Lord Illidan on 2008-03-27
I believe it's mozilla-thunderbird, and yes, Applications->Internet is where you want to go. Have a look at the links in my sig for more information.

---

### Post by Andrew79 on 2008-03-27
Okay, so i looked in the apps>internet, no luck. I understand that some things install themselves, but from that msg i got from the terminal it looks like there is nothing in here for the thunderbird. could i need to do an update to ubuntu? and if so how do i do that? by the way this is still way easier then the vista crap......
thanks

---

### Post by Confuzius on 2008-03-27
You may need to enable the other sources.
Click settings, administration, software sources and go though and check the other sources, multiverse, universe, restricted etc.

This is just by memory, I'm on XP at work, but someone can help you quickly I'm sure.

I think this is the problem.

---

### Post by stchman on 2008-03-27
Yes.

System--->Administration--->Software Sources

Click the main, universe, multiverse, and restricted repos.

Update and go.

---

### Post by Sef on 2008-03-27
Easier is Applications > Add/Remove > Change the box in the upper right to 'All Available Applications'.  Then do a search for Thunderbird.

---

