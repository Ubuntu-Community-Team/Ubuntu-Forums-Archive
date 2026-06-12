---
title: "Reinstalling Video Drivers from recovery"
date: 2005-08-06
forum: Absolute Beginner Talk
---

### Post by Naddiseo on 2005-08-06
Hello, I'm a No0b with linux, I switched a few months ago. 

Anyway, I installed.. or thought I did, some new video drivers so I could play BF1942 without getting errors, I followed the instructions carefully, and now when I reboot it gives me errors about not being able to use the X window system. 

Don't ask what I did, or what drivers, 'cause I really don't remember :'( 

I was hoping that I would be able to reinstall the original drivers from the rescue mode on the CD, but all it gives me is a shell interface.. and I don't know how to use that :oops: 

Any help would be much appreciated.

Rich

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=Naddiseo]Hello, I'm a No0b with linux, I switched a few months ago. 

Anyway, I installed.. or thought I did, some new video drivers so I could play BF1942 without getting errors, I followed the instructions carefully, and now when I reboot it gives me errors about not being able to use the X window system. 

Don't ask what I did, or what drivers, 'cause I really don't remember :'( 

I was hoping that I would be able to reinstall the original drivers from the rescue mode on the CD, but all it gives me is a shell interface.. and I don't know how to use that :oops: 

Any help would be much appreciated.

Rich[/QUOTE]

What card? Where did you get your drivers from?

---

### Post by Naddiseo on 2005-08-07
I have a Radeon 7500.

 I'm not sure where I got the drivers from, I think I got the page from google after doing a lot of searching on how to get BF1942 working. I have an Nvidia, but when I plugged that in it came up with the same error I'm getting now....

---

### Post by poofyhairguy on 2005-08-07
[QUOTE=Naddiseo]I have a Radeon 7500.

 I'm not sure where I got the drivers from, I think I got the page from google after doing a lot of searching on how to get BF1942 working. I have an Nvidia, but when I plugged that in it came up with the same error I'm getting now....[/QUOTE]

Whats the exact error (please)?

---

### Post by Naddiseo on 2005-08-07
[QUOTE=poofyhairguy]Whats the exact error (please)?[/QUOTE]
 > I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Then there's a yes and no option, but it wont let me click either as the shell is over top of them. :S

---

### Post by Naddiseo on 2005-08-07
Sorry to double post, but I really don't know what to do.

Is there anyway I can copy the original drivers off the installation cd? I have access to the shell...

---

### Post by Naddiseo on 2005-08-07
[QUOTE=Naddiseo]Sorry to double post, but I really don't know what to do.

Is there anyway I can copy the original drivers off the installation cd? I have access to the shell...[/QUOTE]
 Fixed :D I reinstalled Xserver-org via apt-get

---

