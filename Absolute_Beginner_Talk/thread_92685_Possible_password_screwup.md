---
title: "Possible password screwup"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-11-20
So, a friend (soon to be former friend) visits from out of town and, since he's a Debian guru, I ask him to solve a few problems I was having. He had a heart attack when he found out there's no separate root password, and promptly made one for me.

He didn't read the Wiki, but I since have, and see that "Note: This is not recommended! It will break all the GUI admin tools." Following--incorrectly following?--the Wiki instructions, I typed sudo therootpassword -l root and it prompted me for my password. I used my "normal" password and got:
sudo: therootpassword: command not found

So then I typed sudo passwd -l root and it returned:
Password changed.

I emailed the soon-to-be-former friend about it, but he hasn't answered.

So, what did I do? Have I changed the root password but it still exists? If so, what did I change it to? I suspect I may have changed it to my normal password. Is that possible?

I want to get rid of it--or lock it, as the Wiki says. But I'm afraid to do anything on this system, in case I screw it up worse.

---

### Post by thomas.mcmahon on 2005-11-20
Hey editrix,

Don't panic, as long as you haven't changed the root password to something you can't remember everything is ok.

Can you still use sudo?

---

### Post by DMVMark on 2005-11-20
I have the opposite problem with passwords.  I have trouble getting into administrator mode when I need to to put wallpapers where I want them and things.  How do I get to work in root long enough to set things the way that I want them?

---

### Post by steve.horsley on 2005-11-20
[QUOTE=editrix]So then I typed sudo passwd -l root and it returned:
Password changed.

So, what did I do? Have I changed the root password but it still exists? If so, what did I change it to? I suspect I may have changed it to my normal password. Is that possible?

I want to get rid of it--or lock it, as the Wiki says. But I'm afraid to do anything on this system, in case I screw it up worse.[/QUOTE]

This locked the root password. Use the command **man passwd** to see for yourself. What no-one tells you is that you type "q" to quit the man page.

As far as I can tell, having a useable root password doesn't harm the admin utils, but I guess they won't work if you try and invoke them while you are logged in as root.

Steve

---

### Post by earobinson on 2005-11-20
Nope it should all work fine.

also you if sudo works you should be able to use sudo su to get into root mode anyway :)

---

### Post by editrix on 2005-11-20
Wow, guys, thanks for all the quick responses!
> **thomas.mcmahon]
Don't panic, as long as you haven't changed the root password to something you can't remember everything is ok.[/QUOTE]

I'n not sure what I changed the root password to, if anything. I wasn't expecting the command line to say "password changed." I thought it would say "root locked" or something.

> Can you still use sudo?

Yes, with my "original" (non-root) password. That is, I tried it with apt-get and it didn't yell at me.

[QUOTE=steve.horsley]This locked the root password. Use the command man passwd to see for yourself.[/QUOTE]

Oh, first thing I did was run to the man page. Clear as mud, as usual. So "password changed" is the same as "root account locked"?

> What no-one tells you is that you type "q" to quit the man page.

There's tons of stuff no one tells you, as I'm continually learning  said:**
> 
  Nope it should all work fine.
 
 also you if sudo works you should be able to use sudo su to get into root mode anyway

I know there are some things that you can't use sudo for, but actually have to switch to root. Is that what you mean?

Oh dear, I'd just like to get things back to the way they were. I suspect this will return to bite me in the you-know-where sometime in the future if I don't.

---

### Post by steve.horsley on 2005-11-20
[QUOTE=editrix]
Oh dear, I'd just like to get things back to the way they were. I suspect this will return to bite me in the you-know-where sometime in the future if I don't.[/QUOTE]

I think they **are** back the way they were. The root password is locked, as it is upon install. I just tried it myself, and it says password changed. It just doesn't say changed to something impossible. Actually, I'm surprised it said anything - the normal unix way is for a succesful command to return without saying a thing - only complain if there's a problem.

If you ever need to be logged in as root, the easiest way is to open a console and type **sudo su** or **sudo bash**. This gives you a true root prompt.

Actually, there's no harm in having a valid root password, just not much point, and an intruder may one day guess it succesfully.

Steve

---

### Post by editrix on 2005-11-20
[QUOTE=steve.horsley]I just tried it myself, and it says password changed. It just doesn't say changed to something impossible. Actually, I'm surprised it said anything - the normal unix way is for a succesful command to return without saying a thing - only complain if there's a problem.[/QUOTE]

Thanks so much for this Steve, it's exactly what I needed. Someone braver than I to try it, and tell me the message is correct, if unfathomable. My stress levels are sinking as I type.

> If you ever need to be logged in as root, the easiest way is to open a console and type **sudo su** or **sudo bash**. This gives you a true root prompt.

I have copied this and pasted it into my e-notebook.

Thanks again. Hmm... There's no icon for Whew!

---

### Post by thomas.mcmahon on 2005-11-20
Glad to see that you have your problem solved.

For the sake of completeness, sudo -s will also give you a root shell.

---

