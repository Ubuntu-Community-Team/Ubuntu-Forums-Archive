---
title: "Grub customization"
date: 2014-05-15
forum: Any Other OS
---

### Post by LastDino on 2014-05-15
So, I've one machine dual booting Fedora 20 as main and Manjaro OB as 2ndory OS. I've installed grub customizer into fedora but I'm not able to change grub wallpaper. 

I've already tried changing picture to png format and reduce resolution to 800x600. Still no result. 


Any ideas?

---

### Post by Cavsfan on 2014-05-15
> **LastDino said:**
> So, I've one machine dual booting Fedora 20 as main and Manjaro OB as 2ndory OS. I've installed grub customizer into fedora but I'm not able to change grub wallpaper. 

I've already tried changing picture to png format and reduce resolution to 800x600. Still no result. 


Any ideas?

Try the method in green in my signature to customize your grub screen. You can make the picture your monitor's default resolution and what you display at bootup is only what you want it to display.

---

### Post by LastDino on 2014-05-16
> **Cavsfan said:**
> Try the method in green in my signature to customize your grub screen. You can make the picture your monitor's default resolution and what you display at bootup is only what you want it to display.


I tried this but it didn't work. After placing the image in /boot/grub2 folder I tried to update grub from terminal with ''sudo update-grub'' but it told me there is no such a command.
I then made (copied) script for it and gave execution permission. But after running it I get error

> /sbin/update-grub: line 3: exec: grub-mkconfig: not found


I'm not sure how to approach this further. Any ideas?

Fyi, I also tried more direct command.
> [QUOTE][glen@localhost ~]$ sudo grub-mkconfig -o /boot/grub/grub.cfg
sudo: grub-mkconfig: command not found
[glen@localhost ~]$ 
[/QUOTE]

---

### Post by Cavsfan on 2014-05-16
> **LastDino said:**
> I tried this but it didn't work. After placing the image in /boot/grub2 folder I tried to update grub from terminal with ''sudo update-grub'' but it told me there is no such a command.
I then made (copied) script for it and gave execution permission. But after running it I get error



I'm not sure how to approach this further. Any ideas?

Fyi, I also tried more direct command.

I have no idea why **sudo update-grub** would not work. You meant you copied your picture to **/boot/grub/** right? 
The fact that grub finds a picture there allows you to set the font and font colors in **/etc/grub.d/05_debian_theme**.
The fact that you cannot run **update-grub** would have nothing to do with the wiki.

Is this a standard install or something else?

---

### Post by LastDino on 2014-05-16
> **Cavsfan said:**
> I have no idea why **sudo update-grub** would not work. You meant you copied your picture to **/boot/grub/** right? 
The fact that grub finds a picture there allows you to set the font and font colors in **/etc/grub.d/05_debian_theme**.
The fact that you cannot run **update-grub** would have nothing to do with the wiki.

Is this a standard install or something else?

I've version 2 of the grub installed so I don't think /boot/grub/ would be the right path as it is *non-existent*. Anyway, you can see whether I've copied the file or not below.


[ATTACH=CONFIG]253208[/ATTACH]

And updating grub is to make it accept changes I just did manually, that is a good practice to get into before you actually boot and see the changes practically. 
Me not being able to update it however, does pose some serious questions irrespective of it being relevant to wiki you linked or not. 

Any ideas?

---

### Post by Cavsfan on 2014-05-16
> **LastDino said:**
> I've version 2 of the grub installed so I don't think /boot/grub/ would be the right path as it is *non-existent*. Anyway, you can see whether I've copied the file or not below.


[ATTACH=CONFIG]253208[/ATTACH]

And updating grub is to make it accept changes I just did manually, that is a good practice to get into before you actually boot and see the changes practically. 
Me not being able to update it however, does pose some serious questions irrespective of it being relevant to wiki you linked or not. 

Any ideas?

Ubuntu uses **/boot/grub/** on every version. This is from Utopic 14.10

[ATTACH=CONFIG]253209[/ATTACH]

Maybe try **sudo grub-install /dev/sda** (where a is the hard drive - a being 1st, b being 2nd, etc.) Then **sudo update-grub**.

---

### Post by LastDino on 2014-05-16
> **Cavsfan said:**
> Ubuntu uses **/boot/grub/** on every version. This is from Utopic 14.10

[ATTACH=CONFIG]253209[/ATTACH]

Maybe try **sudo grub-install /dev/sda** (where a is the hard drive - a being 1st, b being 2nd, etc.) Then **sudo update-grub**.


[ATTACH=CONFIG]253218[/ATTACH]

As you can see, my / is definitely in ext4 but it is telling me it is ext2 and refusing to re-install. Fyi, I did do the re-install from Yum package manager just to check out the theory on the table. It had no effect.

Also, pardon me, I typed out wrong command to update grub on my previous post. Correct command requires you to mention correct version of the grub there, which is grub2. And yes, I did try the correct one.

Now, I'm thinking, what if I installed grub on Manjaro (Partition labelled L2)? Will there be a grub conflict? If yes, what to do to avoid that?

Any other ideas?

---

### Post by Cavsfan on 2014-05-16
> **LastDino said:**
> [ATTACH=CONFIG]253218[/ATTACH]

As you can see, my / is definitely in ext4 but it is telling me it is ext2 and refusing to re-install. Fyi, I did do the re-install from Yum package manager just to check out the theory on the table. It had no effect.

Also, pardon me, I typed out wrong command to update grub on my previous post. Correct command requires you to mention correct version of the grub there, which is grub2. And yes, I did try the correct one.

Now, I'm thinking, what if I installed grub on Manjaro (Partition labelled L2)? Will there be a grub conflict? If yes, what to do to avoid that?

Any other ideas?

It's all grub2 every install on my box is grub2 but that is not the appropriate command. Although you can enter either **sudo update-grub** or **sudo update-grub2** and there is no difference.
Try entering in terminal **man grub2-install** and then try **man grub-install** I'll be surprised in the first one works. The 2nd one should produce output.

---

### Post by Cavsfan on 2014-05-16
I think I am wrong here. I see in Fedora that the command is indeed **grub2-install** but it should produce output by typing **man grub2-install** in terminal.

Here is a link that might benefit you:

[https://ask.fedoraproject.org/en/question/40578/how-to-reinstall-or-fix-grub-in-fedora-20/](https://ask.fedoraproject.org/en/question/40578/how-to-reinstall-or-fix-grub-in-fedora-20/)

---

### Post by LastDino on 2014-05-16
No worries, I've been aware that; on Ubuntu that is the right command as I've used Xubuntu and Ubuntu quite extensively. So, I know where you might be coming from. This is precisely why I'm having trouble, fedora seems to do lot of things differently.

> **Cavsfan said:**
> I think I am wrong here. I see in Fedora that the command is indeed **grub2-install** but it should produce output by typing **man grub2-install** in terminal.

Here is a link that might benefit you:

[https://ask.fedoraproject.org/en/question/40578/how-to-reinstall-or-fix-grub-in-fedora-20/](https://ask.fedoraproject.org/en/question/40578/how-to-reinstall-or-fix-grub-in-fedora-20/)

Out put for the man command
> 
glen@localhost ~]$ sudo man grub2-install
[sudo] password for glen: 
No manual entry for grub2-install



I'll get to reading that tomorrow as its midnight here. I'll post here if I find anything useful. Thanks a bunch.

However, I'm little concerned about Grub reading my ext4 partition as ext2, what are the likely implications other than grub going blind?

---

### Post by Cavsfan on 2014-05-16
> **LastDino said:**
> No worries, I've been aware that; on Ubuntu that is the right command as I've used Xubuntu and Ubuntu quite extensively. So, I know where you might be coming from. This is precisely why I'm having trouble, fedora seems to do lot of things differently.



Out put for the man command



I'll get to reading that tomorrow as its midnight here. I'll post here if I find anything useful. Thanks a bunch.

However, I'm little concerned about Grub reading my ext4 partition as ext2, what are the likely implications other than grub going blind?

Not sure why it was seeing ext2 instead of ext4. This may be a little out of my league. I know the grub wiki works with Ubuntu, Mint and some others; not real sure about Fedora and Manjaro.
I am relatively sure that link should solve your problem. It looked pretty well done to me.

Yeah tomorrow is another day. :) Good luck!

---

### Post by LastDino on 2014-05-19
Unfortunately, I never quite got around to doing this on Fedora and simply installed Grub on my Ubuntu based OS. Grub installed there seems to work better than my expectations, so I'll mark this as solved.

---

### Post by Cavsfan on 2014-05-19
> **LastDino said:**
> Unfortunately, I never quite got around to doing this on Fedora and simply installed Grub on my Ubuntu based OS. Grub installed there seems to work better than my expectations, so I'll mark this as solved.

Good deal! Glad you got a resolution! The latest Grub works really well. 

Good luck. :)

---

