---
title: "problems with 8600gts"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by lachy94 on 2007-10-22
Well, I say I'm having 8600gts problems, but that's just my guess...

Basically, I decided that I should get back on the linux bandwagon, and after not using ubuntu since feisty or edgy, whichever came first, I got gutsy the other day to see what the new release was like.

Firstly I had teething problems with the graphical install and had to grab the alternate version, which I'm sure stems from the greater issue.

Then I got it working, I was in, I had visuals, things were good, I installed the nvidia drivers, the like unsupported ones (whatever the word that gets used for that is, perhaps it starts with r), restarted, and all was still good. The only problem I had was I was stuck with 1280x1024 at best, and my monitor is native at 1680x1050, so I kind of needed to up that. I first off tried to just edit the xorg config, but decided to just run the config program, with sudo dpkg-reconfigure xserver-xorg. After doing this restarting resulted in a black screen that would occasionally flash up some things, that looked like x trying to start up, although I only managed to actually take note of one, which was about initializing batteries :s, so maybe not. Eventually, after about four goes, it would give up, and settle on the black screen, I tried ctrl+alt+f1 and stuff, to try and get myself a terminal, but no luck. I did the non graphical option from grub a few times, and ran the config again, trying some things, like vesa drivers, and taking away the new higher resolutions I had added, leaving the apparently comfortable 1280x1024, but still no luck. In the end I tried to restore the original install, somehow breaking grub, and had to system restore xp just to get back into an operating system :|

Anyway, the thing that seems to cause it all is that when running the xorg config it would try and automatically find a graphics device, and fail. It could happily work out the name of the device afterwards, and obviously it was visible in some way, as it had worked, but the config claimed that xserver could not detect my card. Is this a common thing? Is there a work around? As I almost just thought I was maybe going to have to reinstall windows, and now still have to reinstall linux, I'm a little wary at the moment, but I do want to see this new release, and I believe it should be able to work with my card, it's not that new/special :s

any help will be well received, unfortunately I can not give any logs of the situation :p, as I can't get back into my linux install at the moment, but I'm bound to try again soon and fall into a similar situation and I'll get some

cpu: 6750 core2duo (I was running the 32bit version of ubuntu though, inexplicably)
gfx: 8600gts
mobo: asus p5k
monitor: asus mw221u (if that could mean anything, it detected happily though, so I doubt it)

---

### Post by Pumalite on 2007-10-22
Take a look at this. Figure if it helps you:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

 
When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver

---

