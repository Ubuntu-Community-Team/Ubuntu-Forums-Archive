---
title: "Can't Log On My New Installed Ubuntu 5.04 On Ze2000 pavilion AMD processor"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by charliemerleau on 2005-12-23
Hi to all !

I have been very frustrated over the last 2 months trying to install ubuntu hoary on my ze2000 pavilion notebook with AMD Sempron processor (32 bits). I used the original installation disc ubuntu i386 for intel processor.

During the installation, at the boot prompt, I had to type "linux vga=771" for it to install. the installation then went out smoothly until the system reboot.

GNU GRUB version 0.95
Ubuntu, kernel 2.6.10-5-356

I was prompted to key in my username and password that I did, then the system hang on the next screen. I deleted the partition and started the installation all over again and still the same problem.

What shall I do now? I really want to use Ubuntu but the frustration is getting too much.

Can somebody help me?

Thanks

---

### Post by xmastree on 2005-12-23
Sounds like an X problem. When you entered your login, was it a text screen or graphical? If it was graphical, it may be trying to use a higher resolution than your screen is capable of.
Try ctrl-alt-numerical_plus to change it. If that works, you'll need to go into your /etc/xorg.conf and remove the offending settings.

---

### Post by rooster on 2005-12-23
Hi charliemerleau,

maybe some quotes need a little translation ;) 
[QUOTE=xmastree]
Try ctrl-alt-numerical_plus to change it. [/QUOTE]
This means, try for example CTRL-ALT-F2 to log into a non-grafical terminal to check the functionality of the system. Try if Ubuntu is working at all with, e.g. "ls -l" or any other CLI-Command (CLI = command line interface).
[QUOTE=xmastree]
If that works, you'll need to go into your /etc/xorg.conf and remove the offending settings.[/QUOTE]
This is a little more complicated, it means: if the CLI is working, you have to configure the settings for X (the grafical interface). I will search a link for it.

Keep your head up - a notebook is a little bit more complicated sometimes because of the special (small) parts built in. But it is possible to get it run!

Rooster

---

### Post by rooster on 2005-12-23
[QUOTE=rooster]Hi charliemerleau,
[...]
you have to configure the settings for X (the grafical interface). I will search a link for it.[/QUOTE]
This link to the Ubuntu-Wiki will give you a hint for configuring X: [Fix Video Resolution How To]("https://wiki.ubuntu.com/FixVideoResolutionHowto").

Hope it helps! :D 

Rooster

---

### Post by xmastree on 2005-12-23
[QUOTE=rooster]This means, try for example ctrl-alt-2 [/QUOTE]No... [-X 

I meant Ctrl-Alt-Plus on the numeric keypad (not sure how this works on a laptop, you need to enable certain keys to get the numerical kb) to switch resolution onthe fly. Ctrl-Alt-Minus also does it. Between them they cycle through the available modes.

Try it rooster, I guess you didn't know about that one.

My suspicion is that it's logging in but trying to run too high a resolution. Switching it to a lower one will show if the xserver is running correctly or not.

Nothing to do with Crtl-Alt **F**1-**F**6 for non-graphical terminals.

Although that is also worth a try to see if it's crashed or not.
Note that it's Ctrl-Alt **F2** rather than Ctrl-Alt-**2**.

---

### Post by rooster on 2005-12-23
[QUOTE=xmastree]No... [-X 

I meant Ctrl-Alt-Plus on the numeric keypad (not sure how this works on a laptop, you need to enable certain keys to get the numerical kb) to switch resolution onthe fly. Ctrl-Alt-Minus also does it. Between them they cycle through the available modes.

Try it rooster, I guess you didn't know about that one.[/QUOTE]

Aaah - this is what you meant! You're right - this was new for me! But I'm always trying to learn something new!

[QUOTE=xmastree]My suspicion is that it's logging in but trying to run too high a resolution. Switching it to a lower one will show if the xserver is running correctly or not.

Nothing to do with Crtl-Alt **F**1-**F**6 for non-graphical terminals.

Although that is also worth a try to see if it's crashed or not.
Note that it's Ctrl-Alt **F2** rather than Ctrl-Alt-**2**.[/QUOTE]

:oops: this is happening when I'm sitting in front of my windows laptop and typing by heart and not be able to try it :oops: So I went to the wrong keyboard-line... I'll just edit my former post!

Thanks again xmastree - and merry christmas and a happy new year to you on the Phillipines (a friend of mine was there recently and she was full of joy when she returned!) from Germany!

Rooster

---

### Post by xmastree on 2005-12-23
[QUOTE=rooster](a friend of mine was there recently and she was full of joy when she returned!)[/QUOTE]First time I came here (From UK) I returned full of San Miguel! :) 

Coming from a European county, it does seem strange going to the beach at christmas time. :cool:

Anyway, we're hi-jacking the OP's thread here, we should wait to see if he gets his system running... :rolleyes:

---

### Post by rooster on 2005-12-28
Hi Charlie,

something new from you?

Rooster

---

### Post by charliemerleau on 2006-01-17
Hi all

Thanks so much xmastree and rooster. I am a bit ashamed to visit the forum only today. I think I forgot to specify that the forum should notify me of any post through my email.

I really feel less alone after reading your posts and I must confess I have almost given up on Ubuntu. I will try all your different approaches and let you know the result.

I hope you will still be that willing to reply.

Thanks again

---

### Post by xmastree on 2006-01-17
[QUOTE=charliemerleau]I hope you will still be that willing to reply.[/QUOTE]Of course I will. Always glad to help out where I can, although I may be away for a couple of weeks sometime soon, so if I don't reply, don't take it personally. :rolleyes:

---

### Post by charliemerleau on 2006-01-20
Hi all,

I went back to my ubuntu installation and start all ever again. The first two booting didn’t get me very far; the system hang just on the middle of the first testing screen without any error diagnosed.

I later booted again and this time I was able to reach the *graphical *log in screen. After keying in my username and password, the system hang just like before. I pressed Ctrl - Alt - + as directed by xmastree, still nothing; I also tried Ctrl - Alt - + F2 as Rooster first suggested, no change. No input are consider by the system.

I then shutdown everything and rebooted. This time around, I checked which other button is working. The *reboot* and *shutdown* buttons were ok but when I clicked on *language* or *session*, the system will hang again.

So this is the situation.

Any suggestion as how I can proceed?

Thanks

---

### Post by xmastree on 2006-01-20
Strange...

I re-read your first post and see it's a laptop. I think you might have better response asking in the [laptop forum.]("http://ubuntuforums.org/forumdisplay.php?f=63") rahter than here. Perhaps include a link to this thread in your post.

Something else you might try if possible is installing 5.10 instead of 5.04

I notice you're using the original disc, does this mean you don't have the option to download and burn your own? If you can, try to get 5.10. It might just make the difference.

---

### Post by rooster on 2006-01-20
And maybe another tip:

If you can download and burn a CD, then try to [download]("http://www.ubuntulinux.org/download/") the live CD of Ubuntu  Breezy and set your BIOS to boot from CD before HD.

Maybe you can get another hint from that.

Rooster

---

### Post by charliemerleau on 2006-01-25
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by charliemerleau on 2006-01-25
ok, I will just do as you people suggested. Just one last question, there should be some particular options to take while burning the Cd, something related to  disc image I think. Can someone brief me on that?

I use Nero to burn my Cds.

Thanks

---

### Post by rooster on 2006-01-26
[QUOTE=charliemerleau]ok, I will just do as you people suggested. Just one last question, there should be some particular options to take while burning the Cd, something related to  disc image I think. Can someone brief me on that?

I use Nero to burn my Cds.

Thanks[/QUOTE]

There would be no problem if you'll download the right ISO to your computer. The ISO is a disk image and it depends on your processor which is the right for you. For Intel processors the i386 is mostly ever the right one.
After downloading please check the MD5-checksum of the downloaded *.iso against the checksum in the MD5SUMS-file, currently ```
7fbe948be484ba2f4740ab6113890652  ubuntu-5.10-install-amd64.iso
126751a2dc5528c2f9044d9e4ee36d61  ubuntu-5.10-install-i386.iso
8886a26a1da1daa3669ed6e1253bd93b  ubuntu-5.10-install-powerpc.iso
8523ee4b5490c9b77ac4ec5e5a12b2f5  ubuntu-5.10-live-amd64.iso
49f36f8aef009d6403360de23b5a47d4  ubuntu-5.10-live-i386.iso
752c8d641ca486955c7747cac1c8a305  ubuntu-5.10-live-powerpc.iso

[SIZE="1"](from http://ie.releases.ubuntu.com/ubuntu-releases/5.10/)[/SIZE]
```
This checks the integrity of your file. I hope you know how to check the MD5-checksum?

After downloading and checking the file it is time to burn. I for myself use Nero, too. It is as easy as select "burn disk from image" (I use the german version, so don't ask me of the exact English text) and choose the *.iso-file as the image.

Then just burn it and after verifying ([COLOR="Red"]also important![/COLOR]) your live disk is ready to use.

Just stick your new live CD in your laptop, reboot, go to the BIOS to check if it boots from CD before HD, leave the BIOS and let it boot from the live CD.

Maybe it takes a little time to boot (remember, the CD isn't as fast as the HD of your 'puter) and see if it detects all your hardware and lets you boot into gnome.

Good luck!

Rooster

---

### Post by xmastree on 2006-01-26
[QUOTE=charliemerleau]I use Nero to burn my Cds.[/QUOTE][QUOTE=rooster]Then just burn it...[/QUOTE][http://www.xmastree.34sp.com/ubuntu/burn](http://www.xmastree.34sp.com/ubuntu/burn) explains in detail how to use nero to burn ain image onto a CD.

---

### Post by charliemerleau on 2006-01-27
Thank you rooster and xmastree.

I think I only have to seat down, download and burn the software.
You have provided enough explanations.

Let's wait now for the outcome.

---

### Post by rooster on 2006-01-27
[QUOTE=xmastree][http://www.xmastree.34sp.com/ubuntu/burn](http://www.xmastree.34sp.com/ubuntu/burn) explains in detail how to use nero to burn ain image onto a CD.[/QUOTE]

Nice How-To, xmastree! And good luck, charliemerleau!

Rooster

---

