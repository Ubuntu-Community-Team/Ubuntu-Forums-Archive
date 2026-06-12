---
title: "A few little issue's"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by J-me on 2006-12-25
Hey I new to the Linux scene, I'm tryying to read up as much as possable before I ask question.

I have a number of things that have built up thats I cant find info on and would like to seek help. 

I have 2 version of ubuntu this media centre version which seems to be 6.06 lts and i also have edgy one 6.10. for some unkowen reason the 6.10 version would never install, so I've made do with 6.06 lts.
But lots of things seem to not work, It has crashed at least 12 times within 12 hours, dont mean on the hour im just talking about when im using it. I installed gDesklet and got a ram and cpu read out and it crashs on 100% cpu. Which makes sence I guess but most the time I'm not even doing much as in scrolingl on a web page.
I will post my pc specs to see if anyone can see if I have some kinda hardware prob.

1GHz AMD Athlon
128MB SDRAM (I added 512MB aswell) 640mb in all
nVidia TNT2 M64, TV out
32MB dedicted video memory


At the bottom of the tower it says "hp Pavillion 7865"
I was thinking maybe the mobo cant handle the extra ram?

So anyway thats the main prob I'm having, Next would be sound not getting any dont know where to start for that? The speckers are fine just nicked them from my dell pc.

Most the tutorials I see are for 6.10 so I was thinking of redownloading it and burning it to dvd. But do you think it would be poss just to upgrade this OS. Rather then format and start over as I've got the desktop looking just right. I know I should have bookmarked every where i got stuff didnt think I'd need to upgrade yet.

Last thing I can think of is installing tar.gz files there are laods of tutorials out there but I'm feeling dumb not understanding them. I reckon I can deal with this one on my own but just wanna make sure when a tutorial post code i type it in "Terminal" which I acess via Applications - Accessories - Terminal. I know thats a dumb question but anything i type in there never relates to the tutorial.

Thanks for any help I get!!!!! 
I'm loving Linux apart from all the crashes! [hopefully I'll have that sorted soon (",)]

---

### Post by cilynx on 2006-12-25
Yeah, crashes should not happen.  Period.

Can you give me the output from 
```

free

```

there's a nice hand-holding tutorial on upgrading here:
[http://www.howtogeek.com/howto/ubuntu/upgrading-ubuntu-from-dapper-to-edgy-with-update-manager/](http://www.howtogeek.com/howto/ubuntu/upgrading-ubuntu-from-dapper-to-edgy-with-update-manager/)
basically what it comes down to is
```

gksu &#8220;update-manager -c -d&#8221;

```
it's not hard.

You shouldn't generally have to install tar.gz packages as you'll have just about everything you could ever want in the repositories.  You need a little more background before you should start playing with tgz's.  

Best of luck and welcome to the fold.

---

### Post by J-me on 2006-12-25
Heres the output from when I type "free" in the terminal.

```
 
                total         used         free             shared    buffers     cached
Mem:        645952     306292     339660          0           7144         173844
-/+ buffers/cache:     125304     520648
Swap:       835340          0        835340

```


I know I'm jumping ahead of myself tryying to install .tar,gz files, I'm just loving how much you can change the whole looks of the OS. I wanted to upgrade to firefox 2 and also install a program called "akamaru" both in that format.
I installed 3d desktop that someone recomanded on this forums but havent seen it in any menu since, So I dont know how to run it if synaptic package manager dont leave it in applications menu.

---

### Post by PurplePenguin on 2006-12-25
You say you tried to install some sort of 3D desktop that somebody recommended.  Did this involve installing the nvidia 3D driver?  The only time my computer crashes is due to my 3D acceleration.

My first instinct is always to disable 3D acceleration and see if it helps the situation.

---

### Post by cilynx on 2006-12-25
The output of free there tells you that you've got 640+ meg of RAM functioning.

If you're playing around with compiz and beryl (the 3d desktop candy), there are infintiely many posts on here about what to do.  Just hit up the search and you'll find them.

FF2: [http://ubuntuforums.org/showthread.php?t=284860](http://ubuntuforums.org/showthread.php?t=284860)
Akamaru: [http://www.ubuntuforums.org/showthread.php?t=213786](http://www.ubuntuforums.org/showthread.php?t=213786)

Best of luck

Also, as an aside...  Playing around w/ non-standard applications (ie, anything you can't install using apt-get and without editing your repositories) pretty much guarantees crashes.  Alpha level software just does that.

---

### Post by J-me on 2006-12-25
well that's good to know my ram is fine. 
I didn't try install beryl or anything like that as even I know u need a good gfx card to run it and I don't have one. so someone suggested 3d desktop said it should work on cpu but warned that it is very power hungry. Well as I can't even find it in the menu, I'll uninstall it. I'll let you know if that fixes my probs tomorrow, give it a few hours testing. Thanks for all the help so far.

---

### Post by J-me on 2006-12-26
OK in 2 hours of using its now crashed around 10 times!!!
 
That works out to around 22 hard resets in 2days! I've never had to hard reset this much in my whole life with windows and thats from 1994.

I think ive norrowed it down to firefox, But I cant really be sure as its the program im using everytime it crashes but then again its the only prgram i really use at the mow for research. I've find it would crash faster if I click the bubble for updates when i first boot, But it will crash sooner or later even if I dont click that.

Is there not a fail-safe "ctrl + alt + del" combo I can do when it all freeze? ( ctrl alt and del doesnt work have tried it lol )

I started reading up on how to upgrade to 6.10 a few times but it crashes b4 i get anywhere near doing it. 
Here it goes again.

---

### Post by cilynx on 2006-12-27
Try ctrl + alt + bksp.  That combo kills the GUI assuming the GUI is at all responsive.  It should take you back to login.

---

### Post by hartz on 2006-12-27
Hi there J-me.

I strongly suggest that you use memtest86+ to check your computer's RAM.  memtest86+ is a (small) program which just tests your RAM.  It is a so-called standalone program because it doesn't require an operating system.   

When you reboot your Ubuntu machine, you should get a "grub menu". memtest86+ is typically the last option in this menu.  Select that option and let it do its work - it is pretty much automatic, though it is possible to change some options if you know what you are doing.

Allow it (memtest86+) to run through a few passes and if it reports problems with your memory, try to replace the memory modules.  This will typically take several hours but is definitely worth the wait because it gives you peace of mind regarding the health of your hardware.

If you do not have memtest86+ as an option in your grub menu, search for abootable ISO image on the net, download, burn to disk, and boot from that.

And good luck:-)

---

### Post by J-me on 2006-12-28
thanks again guys I thought you lot had given up on me :)

Yeah when it crashes even ctrl, alt, and back space don't work. :(

I upgraded to 6.10 hoping it would fix my issue but it didn't.
I also run that program last nite, when you said awhile I thought lord of the rings while 3 to 4 hours, not all 3 lord of the ring extened vesion plus the making of... 12hours so far lol :) still waiting.

I need my internet fix for 2day I'm posting from my pda/phone (cant surf the web with this) if its still going by 24hours  I'll post again cryying more :) If its done before I'll post my results.

Thanks again guys for all the help!

---

### Post by hartz on 2006-12-28
The program will run continuously for ever, simply reporting the faults as it finds them.  Basically, it is stress-testing your memory, writing 1s and 0s into memory in different patterns at every address in memory, sequentially, over and over.  The idea is to identify "flakey" memory.

On your display, while memtest86+ is running, you will see an output summary line across the screen.  Near the end of the line, it says something like Std, followed by some numbers.

In the top right-hand corner, you can see the percentage completion of the current "test" and the current "pass" (Each pass is made up of several tests).  Also you will see how many passes has been completed and the number of errors encountered so far on the status/summary line.

In the top left-hand corner you see some nice numbers, such as the throughput from CPU to L1 cache, L2 cache throughput, and throughput to RAM.  Nice to watch, but pretty much meaningless info.  You want to ensure that you get a few passes (eg not less than 2) and that you have zero errors.  Anything other than zero errors is BAD.

A common cause of memory errors on early Socket 939 AMD CPUs is having having 4 double-sided dimms running at 400 MHz.  This was not supported, but could be enabled by forcing the memory bus clock speed in the BIOS.  Don't do this - the extra speed boost is not worth the instability.  Doing this, I used to get memory errors approximately every 3 to 5 passes on my computer, so it is a good idea to test thoroughly.

Check how many passes you have had so far.  If it is more than 3 and zero errors, then your memory can basically be eliminated as the cause of your woes.

Good luck,
  _Hartz

---

### Post by mikewhatever on 2006-12-28
Can you mix RAM sizes like this 128+512? :???: Didin't know that. :-k

---

### Post by J-me on 2006-12-28
well it was running for around 19 hours with 15 passes and 0 fails so thats all good.

I stopped using this pc a while back as i couldn't stand working with 128mb's.
Mate was building his new pc and didn't need his 512 ram so he sold it to me for a tenner, Thought  it would be a perfect time for me to try Linux as XP is power hungry and its only 1ghz pc.

I would love to be able to use both ram chips but if it stops the crashes I'll gladly get rid of the 128mb not the 512mb. I'd rather go back to xp then go that slow.

---

### Post by hartz on 2006-12-28
If memtest86+ doesn't complain about your ram, then keep it like it is.

On newer boards with dual-channel memory, the dimm configuration is more particular.  On older boards, the rule of thumb used to be "put the dimm with the lower speed into the first dimm slot" - this would make all memory modules be configured to run at the lower speed.

But again, your problem is not related to the memory if it has passed 15 full passes of memtest stress testing.

The next most likely candidate is the power supply. :-)

But you can also try to re-install.  Linux is generally rock-solid.

---

### Post by J-me on 2006-12-28
i didn't know that rule of thumb :-k  but I do now.

I had the 512 in the first and the 128 in the second, I pulled the 128 out to see if it would make a diff  and it hasn't crashed in 15 mins!!!!!!!! 
So i might try put the 128 back into the first slot next time I power down the pc.

Thanks guys !!!!!!!!!!!!!

---

### Post by J-me on 2006-12-30
Yeah I spoke to soon :( 

But it lasted a hell of a lot longer then normal. Before I would have been lucky to get 10 mins, But it crashed after 2hours!!!!!!! which is better but I'd rather it didn't crash at all I but just get rid on ubuntu on my hp and see if I can nick my bros old laptop and give it ago.

Thanks guys for all the help =) I'm sure you will see loads of post of me asking stupid questions when I get going on my bros laptop.

---

