---
title: "Shutdown Problems!"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by squee on 2006-07-15
Hey,

I am a complete n00b and not afraid to admit it. My problem is that when i try and shutdown the pc it gets to the line   " will now halt ". The harddrives turn off but the fans and the monitor are still working.

With a little help from the IRC, i ran dmesg(?). Thats about as far as I got  ](*,) . If anyone replies to this, can they please include a lot of detail.

Thanks!!!

Squee

p.s Im running ubuntu 6.06   and this whatever it means  2.6.15-26-686
looks important though so I though I'd include it. Thanks again!

---

### Post by skale on 2006-07-15
go to the terminla and type either s**udo halt** or **sudo shutdown -h now**. See if it shuts down.

---

### Post by squee on 2006-07-15
I've tried shutdown now   but that only gives me the same problem. The IRC said it was something to do with my GRUB menu or something like that. Anyway, i'll give that a go. I'll let you know if it doesnt work! :) 

Thanks.

---

### Post by squee on 2006-07-15
No sorry that didn't work. Same result. I read on another thread that it was something to do it my kernel. I checked and im running ...686, one of the problem ones stated in that thread along with K7. Hope this helps you help me!

Any other ideas?

Thanks,
Squee

---

### Post by skale on 2006-07-15
Strange... Maybe you have one of those computers where you have to cut the power yourself. Has it ever said "IT is now safe to turn off your computer" before you installed ubuntu? Just shooting in the dark here...

---

### Post by squee on 2006-07-16
No. I just updated to 6.06 but i was using the previous one before that and it worked fine. Before that I was using Windows 98 and shutdown again worked fine. 


Someone mentioned I might need to edit the GRUB menu. How do I do that?


Thanks,

Squee

---

### Post by arkangel on 2006-07-16
to  edit grub  you need to go  to /boot/grub/ and edit  menu.lst 
there are some option for apci  and other stuff that might solve your problem 
(with no care it 'll be a total mess in your system )

please read [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
before  guessing  :)

---

### Post by h2gofast on 2006-07-16
I wouldn't edit grub just yet.  If you're having trouble with a shutdown, editing grub incorrectly would really obscure the problem.
"sudo shutdown -h now" should shut it all down.  On some desktops it will shut everything down, but you still need to hit the power switch after ubuntu has closed itself down.

Is this a laptop or desktop?  Can you say which model, and if you built it yourself, which motherboard?

---

### Post by Sef on 2006-07-16
Possibly it's  powermanagement problem.  To fix that you would need to go into the BIOS and find it.  If you are not sure how to do that, let me know and I (or someone else) will give you some more directions.

---

### Post by squee on 2006-07-16
I dont really understand the whole menu.lst script even with the help of that site. Would entering the Grub menu at start up help?

---

### Post by squee on 2006-07-16
> **Sef said:**
> Possibly it's  powermanagement problem.  To fix that you would need to go into the BIOS and find it.  If you are not sure how to do that, let me know and I (or someone else) will give you some more directions.


Yeah that would be great if you could give me some help. Thanks!

---

### Post by squee on 2006-07-16
The computer Im using is a P3 desktop. It was being thrown out at my mams work and ive rescued it and upgraded it with a new dvd drive but thats about it. Not sure what motherboard it is. Is there anyway of finding out through Ubuntu?

---

### Post by Sef on 2006-07-16
> The computer Im using is a P3 desktop. It was being thrown out at my mams work and ive rescued it and upgraded it with a new dvd drive but thats about it. Not sure what motherboard it is. Is there anyway of finding out through Ubuntu?

To check how much memory you have do this:  System > Administration > System Monitor > Resources

> Possibly it's powermanagement problem. To fix that you would need to go into the BIOS and find it.

Upon start up, you need to push either F2, Delete, or Esc.  It will tell you what to push to enter the BIOS.  Then check for the powermanagement and see if it is set to ON.

---

### Post by squee on 2006-07-16
When upgrading it, my friend added some old sticks of Ram so thats why its a bit weird. Not all of it works properly but I've never had any trouble with shutdown before.   system monitor says 

User memory 140.8   of   502.9 MiB
used swap   0 bytes of   760.9 MiB

I tried to edit the BIOS under power management and it was disabled so i changed it to Min settings. under the user default everything underneath it was disabled.  If you need anyother information, can you tell me how to get it as well just in case i dont know!

Thanks.

---

### Post by squee on 2006-07-16
Im still waiting for a reply from anyone who knows, about my shutdown problem.

Thanks

---

### Post by franute on 2006-07-17
I also have problems with shutdown. I get the message "will now halt" and then, I have to push the power button, after editing the grub deleting "splash", It said:
"will now halt"
"[*numbers*,*numbers*]Power Down"

I think that turning off the "acpi" and "apm" in the grub menu, it worked (I did it time ago), but I have a laptop and I need them. In Suse 10.1, it shutdowns perfect with the kernel 2.6.16, maybe that's the problem?? should I recompile my kernel with a newer one?? Thanks



PS: sorry about my grammar, I'm not english :-?

---

### Post by squee on 2006-07-17
> **franute said:**
> I also have problems with shutdown. I get the message "will now halt" and then, I have to push the power button, after editing the grub deleting "splash", It said:
"will now halt"
"[*numbers*,*numbers*]Power Down"

I think that turning off the "acpi" and "apm" in the grub menu, it worked (I did it time ago), but I have a laptop and I need them. In Suse 10.1, it shutdowns perfect with the kernel 2.6.16, maybe that's the problem?? should I recompile my kernel with a newer one?? Thanks



PS: sorry about my grammar, I'm not english :-?
Your English is better than most people I know who have been speaking it all their lives. I wouldnt have known if you hadn't said. I have to be really careful now ;-)

Im using Kernel  686 and this is the only problem I've had with it so far (2 weeks). Im dont know if you should upgrade; ask others first and get a better opinion. I've read a lot of other posts on how to fix my problem but none seem to work for me.

---

### Post by tseliot on 2006-07-17
> **squee said:**
> Im still waiting for a reply from anyone who knows, about my shutdown problem.

Thanks

Did you install the Nvidia driver?

If so, please read point 13 of the problems section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by squee on 2006-07-17
> **tseliot said:**
> Did you install the Nvidia driver?

If so, please read point 13 of the problems section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
I think so, yes. I have a NV4 RIVA TNT. This seems to be on your list of unsupported cards. What should I do about that? At the moment I think I have the nvidia glx legacy  driver, but I'm not sure. I followed point 13 and I'll reboot after i have posted this.

Thanks in advance if this works


still not working. I do have nvidia glx legacy. After Will now halt, I got this message: [139.844464] power down

---

### Post by squee on 2006-07-18
I got it to work! :) 

Still not 100% sure how. I disabled the Splash on shutdown and did something with the nVidia drivers (not sure though) and it now works. If any of this is down to you, thanks!!! :D

---

