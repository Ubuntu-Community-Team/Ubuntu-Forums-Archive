---
title: "Safe Mode?"
date: 2009-05-16
forum: Apple Hardware Users
---

### Post by N00b007 on 2009-05-16
Hi, 

I just installed ubuntu 9.04 on my Macbook(dual boot with OS X). Then I installed CompizConfig Settings Manger (ccsm), and started customizing the settings in ccsm. All of a sudden all the windows that were opened turned black as well as all the toolbar. This keeps happening when I startup ubuntu. So I can not even use ubuntu. 

Also ubuntu works with my airport wireless, but it is extremely slow and is choppy(drops the signal periodically). 

Any help will be greatly appreciated. Thanks.

---

### Post by cyberdork33 on 2009-05-16
in the grub screen there should be an option to boot into recovery mode.

---

### Post by N00b007 on 2009-05-16
When I choose "recovery mode" it takes me to a screen with many options: continue boot normally, ..., xfix auto fix graphic problems. I tried some of these options but they just boot me in normally, and I still have the same problem. 

Thanks

---

### Post by N00b007 on 2009-05-18
Can someone please help me. I can not use Ubuntu.

---

### Post by damis648 on 2009-05-18
Boot up in Ubuntu, ever though you probably cannot see much. Once you are sure you are fully logged in, press Alt+F2 and type
```
metacity --replace
```
and hit enter. Everything should turn back to normal, with no compiz. Go into CCSM and reset the settings, then turn visual effects back on.

---

### Post by N00b007 on 2009-05-18
Thank You for the reply. Unfortunately when I login in and hit Alt+F2 nothing happens. The screen is still partly black. This may be because I have a Macbook 1.1 and F2 is the brighten screen button. So I went into grub and booted into recovery then selected root shell CLI, and typed in 'metacity --replace' and it responded 'unable to open X window' (something like that). Still not sure what to do. BTW how do you shut down the computer or restart the computer while in root CLI mode. 

Thanks for any responses.

---

### Post by cyberdork33 on 2009-05-19
> **N00b007 said:**
> Thank You for the reply. Unfortunately when I login in and hit Alt+F2 nothing happens. The screen is still partly black. This may be because I have a Macbook 1.1 and F2 is the brighten screen button. So I went into grub and booted into recovery then selected root shell CLI, and typed in 'metacity --replace' and it responded 'unable to open X window' (something like that). Still not sure what to do. BTW how do you shut down the computer or restart the computer while in root CLI mode. 

Thanks for any responses.
If F2 is brightness, then you need to use Fn+F2 to get F2.

To do what damis was suggesting, you will have to login to the desktop blindly. Using the Alt+F2 combo will open a run box in gnome, but since you display is not showing anything, you will not be able to see it. In that run box, you type 'metacity --replace' and RETURN and the display should suddenly work again.

PS, the reboot CLI command is 'reboot' and the shutdown command is 'shutdown'. To turn the compture completely off though, you would run 'shutdown -h now'.

---

