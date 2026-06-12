---
title: "Live CD Freexes at Desktop"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by USR612 on 2007-03-24
Whenever I try to,oad ubuntu from the live cd everything goes fine until the dektop loads up.  At this point the computer seems to freeze, not letting me move my mouse or use my keyboard.  Any suggestions on how to fix this problem would be greatly appreciated (I'm running a Presario SR80NX).

Note: I'm entirely new to linux so please forgive me if I appear to be completely stupid.

---

### Post by rocknrolf77 on 2007-03-24
No question is stupid. It's a friendly forum. What graphics card do you have? What release did you download? Welcome. :)

---

### Post by j.miller565 on 2007-03-24
maybe try the alternaate cd. That should definatly work :-)

---

### Post by USR612 on 2007-03-25
Thanks for the useful help,
Sorry about the lack of information.  I tried downloading ubuntu 6.10 adn I have whatever graphics card came with the computer (something about an Intel graphics media accelertor 950?).  This may not be the information needed to find a fix but I'm new to Vista and find it irritatitng to try and find any info on my computer.

I forgot to try the alternate CD (Oops) so I'll make that my next step.  Thanks again for the all the help.

---

### Post by wpshooter on 2007-03-25
First, did you test the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Have you tried booting with the safe graphics mode parameter ?

Good luck.

---

### Post by kittyhawk63 on 2007-03-25
> **USR612 said:**
> Whenever I try to,oad ubuntu from the live cd everything goes fine until the dektop loads up.  At this point the computer seems to freeze, not letting me move my mouse or use my keyboard.  Any suggestions on how to fix this problem would be greatly appreciated (I'm running a Presario SR80NX).
Note: I'm entirely new to linux so please forgive me if I appear to be completely stupid.
  I take it that you downloaded the Live CD. What speed did you burn the ISO to your CD?
It should not be any faster than 4X. If it is, you may encounter problems. Reburn it at 4X or slower to make sure you have a good working copy.
kh

---

### Post by kittyhawk63 on 2007-03-25
> **USR612 said:**
>  Note: I'm entirely new to linux so please forgive me if I appear to be completely stupid.

We've all been there. You're not stupid. Your inexperienced in Linux. We welcome you to the forum. In a few short weeks, I have been helped tremendously by this forum. Notice the number of threads (Beans) that I have run already. I've received help to resolved all my questions so far. Hang in there.
kh

---

### Post by USR612 on 2007-03-25
I tried burning the CD at the lowest speed it would allow me to, and after checking the disk it tells me everything went fine, and to 'press any key to reboot your system'.  At this point the computer freezes again, and nothing on my keyboard will work.  Only way out is a hard reboot.

---

### Post by oilchangeguy on 2007-03-25
please advise your systems specs.

---

### Post by USR612 on 2007-03-28
Sorry again about the lack of info, and the time taken to respond.
I have a new, but similar problem now.  I managed to install ubuntu fine from the alternate cd.  It even detected my Vista installation so now I can dual boot, (something I had been told would be impossible without modifying GRUB), but now whenever I load into ubuntu it freezes at the screen that says 'Ubuntu' with the bar that's supposed to flash across, or whatever it does.  Once again thanks for all the eplies (nice to be on such a friendly forum) and any suggestions would be much appreciated.
-
1 gig. Ram
2.8 gigahertz pentium D processor
what I know about my graphics card (very little) has been posted already
Probably not relevant, but I parttioned 60gb for the ubuntu install and about 4gb for swap.
-
Thanks

---

### Post by kittyhawk63 on 2007-03-28
> **USR612 said:**
> Sorry again about the lack of info, and the time taken to respond.
I have a new, but similar problem now.  I managed to install ubuntu fine from the alternate cd.  It even detected my Vista installation so now I can dual boot, (something I had been told would be impossible without modifying GRUB), but now whenever I load into ubuntu it freezes at the screen that says 'Ubuntu' with the bar that's supposed to flash across, or whatever it does.  Once again thanks for all the eplies (nice to be on such a friendly forum) and any suggestions would be much appreciated.
-
1 gig. Ram
2.8 gigahertz pentium D processor
what I know about my graphics card (very little) has been posted already
Probably not relevant, but I parttioned 60gb for the ubuntu install and about 4gb for swap.
-
Thanks

There is something called m5sum (?) that allows you to check your CD against the file on the Internet. It will let you know if your CD data is okay. Check that out here on the forum.
I am too new to help you further. I'm sorry.
kh

---

### Post by NeoGreen on 2007-03-28
I was having the same problem.  What burner program are you using?  I recommend CD Burner XP Pro3 (its free).

---

### Post by USR612 on 2007-03-29
Thanks for the replies, just a (stupid) question for NeoGreen.  I guess if I burn the cd with this program I have to re-install it? Is/are there any other trick(s) to learn? Thanks.

---

### Post by BillGod on 2007-03-29
you might want to try hitting f6 at the boot menu.  a script with a bunch of stuff will come up.  add noapic nolapic to the end of it and hit enter and see if it loads ok for you.

---

### Post by USR612 on 2007-03-29
Thanks for the tip, but I'm not loading from the live cd, but from the hard drive.  The boot menu comes up fine, and I can load into Vista perfectly but ubuntu does not seem work right.
I also tried downloading CD Burner XP Pro 3 but it doesn't seem to recognize my cd drive, (maybe not meant for Vista?).

---

### Post by NeoGreen on 2007-03-29
Sorry, I didn't realize that you were using Vista:(   What you can do is use the burner Vista comes with.  When you download the ISO, it will automatically be downloaded into your download folder, from there all you have to do is highlight the ISO you want to burn and press the burn button on at the top.  You will be prompted to insert disk and then it will burn it for you.  Sorry about CD Burner XP, I thought you were using windows XP.  Hope this helps.

---

### Post by USR612 on 2007-03-29
I really appreciate the tip!  I've been using Roxio media creator but from what I hear, it has some less than desireable qualities.
I just want to make sure I've got this right;
If I burn ubuntu using this method, uninstall it and then reinstall it using the new disc, it should work? Thanks.

---

