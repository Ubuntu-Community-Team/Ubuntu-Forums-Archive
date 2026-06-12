---
title: "Gutsy Live cd booting"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by jimmer0355 on 2007-10-18
Just downloaded and burnt the Gutsy final release cd. When I boot to it I get the Ubuntu flash screen and it continues on but just before I here the music my monitor powers off then i here the music. 

I have been working with the gutsy beta release and doing all the updates as I go and it works fine. But only with the final release running from the cd do i have this problem. Now when I power my monitor back on my monitor displays no video signal.  I have tried it on 2 more identical systems and the same thing happens with thesen the 2 systems there is no hardware difference. The only difference is that they have Edgy installed.. 

Got me scratching my head.

---

### Post by mikeyphi on 2007-10-18
Can only suggest a 'bad' CD - I've just installed Gutsy with no probs.

---

### Post by pchr on 2007-10-18
Hello jimmer0355 I get the same.  I'm guessing it's setting a resolution too high for my monitor or something like that.  I can get it working if I escape at the main menu and then type :

live vga=0x31A

(for a 1280x1024 resolution)

My worry is that if I install the software I'll have the same problem, not sure what to do if that's the case, so far I've found that you can edit grub as you boot up by adding vga=0x31A in the right place but on my current installation that seems to only effect the bootup resolution.

You get anywhere?

---

### Post by eldragon on 2007-11-10
i have had the same problem with every computer ive thrown the cd at..

its a great issue i must say, since livecds should be focused on newcommers, who wil be discouraged to follow through if they need to start typing boot commands on the live cd..

is there a permanent fix on the way? or is the final cd already "pressed" and theres nothing we can do officially... :(

this is a main issue, since i usually giveaway livecds to people who come around and ask if im using vista (really..this usually happens)...

btw: could you give a little more info on what "live vga=0x31A" does? 

thanks..

---

### Post by mivo on 2007-11-10
Another thing to try:

In the start-up menu of the Live CD (where you are asked what you would like to do), press F6. A line of text appears at the bottom. Here, replace "splash" with "nosplash" and remove "quiet". Hit enter and see if this fixes the trouble. :)

---

### Post by eldragon on 2007-11-23
i have to apologize.

only thing in common with all the computers ive thrown the cd at, is they were sharing the same monitor, for some reason the gutsy live cd doesnt like old monitors.

ive changed it to a better screen and the problem has gone away, althought the vga boot mode should have worked, it never did.

still an issue, not that big an issue i must say. but an issue.

cheers.

---

### Post by nikef on 2007-11-23
Hi 
do you have a flat monitor?
theres a post around here somewhere that may be of help to you,i will go and look for it and post it here
for you

---

### Post by nikef on 2007-11-23
Here is the post,i am not sure if it will help you,hope it does 

[http://ubuntuforums.org/showthread.php?t=604216](http://ubuntuforums.org/showthread.php?t=604216)

---

