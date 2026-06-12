---
title: "Network and sharing files in Kubuntu?"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Mathias-K on 2006-01-15
Hi guys.

I feel like i'm almost ready to take the plunge and install Ubuntu/Kubuntu on my laptop as well as my Kubuntuing desktop from which i'm writing now. Then I wanted to move my files over my wired network when it struck me that I didn't know anything about networking in Ubuntu/Kubuntu. How is it done?

I've hooked my WinXP laptop up with a manually set IP adress (that works perfectly between XP-systems) and my Kubuntu desktop also with a manual IP. Then what do I do?:confused: 

I think I've gone through the Wiki and the forums search a dozen times, and i know there has to be an article on it, but where?

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=Mathias-K]Hi guys.

I feel like i'm almost ready to take the plunge and install Ubuntu/Kubuntu on my laptop as well as my Kubuntuing desktop from which i'm writing now. Then I wanted to move my files over my wired network when it struck me that I didn't know anything about networking in Ubuntu/Kubuntu. How is it done?

I've hooked my WinXP laptop up with a manually set IP adress (that works perfectly between XP-systems) and my Kubuntu desktop also with a manual IP. Then what do I do?:confused: 

I think I've gone through the Wiki and the forums search a dozen times, and i know there has to be an article on it, but where?[/QUOTE]

1) Create a shared folder on WinXP.
2) On Ubuntu, open Nautilus.
3) In the location bar, enter "SMB:/<xp-ip-address>/<share-name>"
Hope that helps!

---

### Post by Mathias-K on 2006-01-15
[QUOTE=cwaldbieser]1) Create a shared folder on WinXP.
2) On Ubuntu, open Nautilus.
3) In the location bar, enter "SMB:/<xp-ip-address>/<share-name>"
Hope that helps![/QUOTE]

I'm in Kubuntu, but I'll try it. BTW, is there no easier way than typing code? Not a GUI method like in XP? :(

---

### Post by Omnios on 2006-01-15
One note I found both win and linux firewalls stop networking in its tracks so you may have to write ip rules for them to allow access. I findled around for like 10 min till I figured out the fiirewall was stopping me cold. ALso not shure but you may have to install samba if I remember corectly as samba was for access only but not 100% sure on that. Think that was for winshares though

---

### Post by Mathias-K on 2006-01-15
[QUOTE=Omnios]One note I found both win and linux firewalls stop networking in its tracks so you may have to write ip rules for them to allow access. I findled around for like 10 min till I figured out the fiirewall was stopping me cold. ALso not shure but you may have to install samba if I remember corectly as samba was for access only but not 100% sure on that. Think that was for winshares though[/QUOTE]

Could you please explain that? What's "write ip" - a program, a command? :)

Right now, I am simply amazed by the extreme lack of user friendliness in Kubuntu versus WinXP, so please help me out on this..

---

### Post by Adrian on 2006-01-15
[QUOTE=Mathias-K]I'm in Kubuntu, but I'll try it. BTW, is there no easier way than typing code? Not a GUI method like in XP? :([/QUOTE]

The same thing works in Kubuntu, from Konqueror!

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=Mathias-K]I'm in Kubuntu, but I'll try it. BTW, is there no easier way than typing code? Not a GUI method like in XP? :([/QUOTE]
Ha!  That's the first time I heard of a URL referred to as code!  I guess you want something like Network Neighborhood, though?

You can set that up, but it still usually requires plugging in some configuration numbers, even if you are networking two Windows machines together.

The URL I gave you should work without having to install any other software, but you could try installing the "smb4k" package if you want a more graphical approach to file sharing.

---

### Post by Omnios on 2006-01-15
> Originally Posted by Omnios
One note I found both win and linux firewalls stop networking in its tracks so you may have to write ip rules for them to allow access. I findled around for like 10 min till I figured out the fiirewall was stopping me cold. ALso not shure but you may have to install samba if I remember corectly as samba was for access only but not 100% sure on that. Think that was for winshares though


[QUOTE=Mathias-K]Could you please explain that? What's "write ip" - a program, a command? :)

Right now, I am simply amazed by the extreme lack of user friendliness in Kubuntu versus WinXP, so please help me out on this..[/QUOTE]


 My firewall was blocking the other machines ips so I whent into firestarter / Policy and entered the ip of the other machine into the inbound rule. Basicly I tryed connecting with the other machine and got the address from firestarter when it blocked it.

---

### Post by Mathias-K on 2006-01-15
[QUOTE=cwaldbieser]Ha!  That's the first time I heard of a URL referred to as code![/QUOTE]  

I'd hardly call "SMB:/<xp-ip-address>/<share-name>" a URL. Isn't it more like a command to the SMB program to do something, and not an address?

[QUOTE=cwaldbieser]I guess you want something like Network Neighborhood, though?[/QUOTE]

YES! I simply hate WinXP's rather lame network system full of errors that should not be there, prompts for password that were never created and more sudden errors. I'd like a button named Network that just scanned the neighborhood and gave me no nonsense - one that even my father could use. 

[QUOTE=cwaldbieser]The URL I gave you should work without having to install any other software ...[/QUOTE]

It did, thanks for the heads up :) But, i would never have figured it out alone, which by itself, and even more so combined with the fact that it is not pretty, suggests that it is a place that could be improved - and actually lure some Windows users tired of troubles over :)

---

### Post by Adrian on 2006-01-15
[QUOTE=Mathias-K]I'd hardly call "SMB:/<xp-ip-address>/<share-name>" a URL. Isn't it more like a command to the SMB program to do something, and not an address?[/QUOTE]

In fact, it is an address to the computer you want to access. If you want point and click, you can instead type:
```
SMB:/
```
and navigate using your mouse.

You can bookmark your favourite remote dirs, which elimitates the need of typing.

---

### Post by GoldBuggie on 2006-01-15
To access shares in kubuntu; writing smb:/ in konq. is one way or goto "system places->remote places" is another. The later is only point and click and should be straight forward, It is found in the icon beside the kmenu icon.

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=Mathias-K]I'd hardly call "SMB:/<xp-ip-address>/<share-name>" a URL. Isn't it more like a command to the SMB program to do something, and not an address?
[/QUOTE]
It's a URL.  A URL is basically:
scheme://authority/path?query

So for "http://www.google.com/index.html"
scheme == HTTP (Hypertext Transfer Protocol)
authority == [www.google.com](www.google.com)
path == index.html

For "smb://192.168.0.2/myshare"
scheme == smb
authority == 192.168.0.2
path = myshare

---

