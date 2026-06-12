---
title: "Graphics on HP Pavilion dv9605ea"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by cellarmation on 2007-12-26
Hi, my brother has just bought a brand new HP Pavilion dv9605ea he is hoping to be able to get rid of vista and run Ubuntu Gutsy. Tried running the live cd and the screen wasnt recognised and the failsafe graphics kicked in.

I am not sure which option we need to pick from the list, can anyone help? I think the screen is "17'' Brightview Widescreen Display"

---

### Post by Cypher on 2007-12-26
The DV9605ea seems to come with a NVidia GeForce card and Ubuntu plays well with NVidia video cards. Can you look at the HP documentation to see which GeForce card is exactly in there?

The alternate thing to do is download the Alternate Ubuntu CD (text-based installer) and install Ubuntu on the notebook and then install the restricted-drivers for NVidia and see if that fares better..perhaps the updated drivers better support the video card than the ones on the LiveCD..

---

### Post by cellarmation on 2007-12-26
Yeah i think the problem is it just doesnt know what the screen is and i need to pick an option or something. The side of the box we just took it out of says "nVidia GeForce 7150M with shared graphics memory"

Think its also having problems loading the broadcom drivers for the wireless if we try to proceed using the failsafe graphics, but i guess i will worry about that a bit later on lol. Thanks for helping :-)

---

### Post by Cypher on 2007-12-26
Ahh OK..as far as the screen goes, you might want to start off conservative and tweak it later on once Ubuntu is fully installed.

Not having installed Ubuntu on a laptop, I'm a little lax on personal experience here..so hopefully someone else will jump in here..

---

### Post by cellarmation on 2007-12-26
Ok sure, thanks for replying so quickly anyway.

---

### Post by FreakTech on 2007-12-26
I have gusty running on a dv8235nr HP and I had the same problem with the live cd.  Once it's installed you shouldn't have a problem with the restricted driver manager.   

As far as the broadcom, I have an HP nc6320 that uses the broadcom and the restricted driver manager took care of it also.

Good luck.

---

### Post by cellarmation on 2007-12-26
> **FreakTech said:**
> I have gusty running on a dv8235nr HP and I had the same problem with the live cd.  Once it's installed you shouldn't have a problem with the restricted driver manager.   

As far as the broadcom, I have an HP nc6320 that uses the broadcom and the restricted driver manager took care of it also.

Good luck.

Is there anyway to boot the live cd without it trying to load the broadcom drivers? Or do i need to do something like the text based install as it doesnt seem to want to load the live cd.

---

### Post by FreakTech on 2007-12-26
I didn't have a problem with the live CD loading.  Are you getting an error or is it just hanging?

---

### Post by cellarmation on 2007-12-26
It has managed to boot successfully under the second option with failsafe graphics.

When i pick the first option, then pick failsafe graphics when asks me latter on, it doesn't seem to finish booting. (it gets about 4 broadcom errors in a row and stays at a command prompt) strange.

Might try installing soon, and playing around with the screen settings. Thanks.

---

### Post by cach0rr0 on 2007-12-29
first post!

i got one of these 2 or 3 days ago from Currys, and decided to do my first ubuntu install after being a die-hard gentoo user since 2005. just didnt feel like the trouble of trying to get all these gadgets to work under gentoo :P

anyways, i ran into the same thing, did some tinkering and got around it

-hit CTRL+ALT+F3 to return to the terminal
-run **X -configure** which will generate xorg.conf.new
-remove /etc/X11/xorg.conf and replace it with the newly-generated xorg.conf.new
-type **/etc/init.d/gdm restart** at the terminal to enter your livecd/install environment, and install as per usual

worked fine for me this way. hope it helps someone else!

once you get the environment installed, itll run in low graphics mode...no worries there, as soon as you enable the restricted driver and reboot, it all returns to normal, and you can go in and install compiz and do all of that fun desktop effects gibberish

now to see if i can find the right windows driver for the broadcom wireless card :)
back to hunting. if anyone knows offhand where I can snag this, greatly appreciate it.

**edit:**nevermind. i think i may have found the driver, just cant get the bugger working, pulling an address, etc

---

### Post by SteveGodfrey on 2008-01-12
I have the dv9605ea and it's working a treat.

I installed using the alternate CD (text install), the 'restricted drivers' graphics driver works brilliantly. Same couldn't be said for the broadcom wifi. I got that working using the ndis wrapper with the XP dirver, the vista driver from the HP site didn't work.

---

### Post by cellarmation on 2008-01-19
> **cach0rr0 said:**
> first post!

i got one of these 2 or 3 days ago from Currys, and decided to do my first ubuntu install after being a die-hard gentoo user since 2005. just didnt feel like the trouble of trying to get all these gadgets to work under gentoo :P

anyways, i ran into the same thing, did some tinkering and got around it

-hit CTRL+ALT+F3 to return to the terminal
-run **X -configure** which will generate xorg.conf.new
-remove /etc/X11/xorg.conf and replace it with the newly-generated xorg.conf.new
-type **/etc/init.d/gdm restart** at the terminal to enter your livecd/install environment, and install as per usual

worked fine for me this way. hope it helps someone else!

once you get the environment installed, itll run in low graphics mode...no worries there, as soon as you enable the restricted driver and reboot, it all returns to normal, and you can go in and install compiz and do all of that fun desktop effects gibberish

now to see if i can find the right windows driver for the broadcom wireless card :)
back to hunting. if anyone knows offhand where I can snag this, greatly appreciate it.

**edit:**nevermind. i think i may have found the driver, just cant get the bugger working, pulling an address, etc

Im glad to see some other people have been having some success with this model.

I can confirm that we managed to get the restricted drivers working very easily but the problem we had was X finding a suitable panel option, it wouldn't suggest anything other than plug and play monitor. We went through picking lots of different options but couldn't get one to get him over a resolution of 1024*768, not even wide screen :(. So his computer is very strange, low resolution, but with nice desktop effects!

What screen option are you guys using, is there anyway for us to make our own one or something?

We gave up with the broadcom after a lot of effort, SteveGodfrey is there anything you did in particular to get the ndis wrapper to work? I can't remember exactly, but im sure we tried that and got no where.

---

