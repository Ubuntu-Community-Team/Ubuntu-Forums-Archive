---
title: "Four random questions about all kinds of stuff..."
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by some_random_noob on 2006-11-20
- My lcd is running at 75hertz in ubuntu, and in windows xp the max is 70hertz (unless I click "display refresh rates that the monitor cannot display") Is that going to kill it any faster?

- Does edgy eft let you change the refresh rate?

- Does edgy eft make it any easier to get a dvd drive to work?

- If you can't do the two above things, is there any chance we'll see these features soon? Because they should be easy and it pisses me off.

Thanks to anyone who has read this, you've probably wasted your time. I just need some idea of when these things will actually happen with ubuntu (obviously no time soon) I don't have the time to sort out the refresh rate/dvd drive now... maybe some other time, however I will accept links to any useful tutorials :D

](*,)

---

### Post by IYY on 2006-11-20
> - My lcd is running at 75hertz in ubuntu, and in windows xp the max is 70hertz (unless I click "display refresh rates that the monitor cannot display") Is that going to kill it any faster?

It's probably fine, but just to be safe it's always a good idea to edit your /etc/X11/xorg.conf file and enter the correct horizontal and vertical refresh rates (range). You can find these in your monitor's manual or on the monitor's website.

> Does edgy eft let you change the refresh rate?

Yes, and so does Dapper and Breezy. It's under System > Preferences > Screen Resolution. However, if your horizontal and vertical range is not set up correctly for your monitor, it might not display all resolutions your monitor is capable of. If set up correctly, all choices should appear there.


> - Does edgy eft make it any easier to get a dvd drive to work?

No, but it's not difficult at all. Just follow the instructions in the Ubuntuguide. It's just a matter of copying a few commands into the terminal! 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability)

> - If you can't do the two above things, is there any chance we'll see these features soon? Because they should be easy and it pisses me off.

Sorry, but no. The DVD playback issue is not a technical but a legal one. It simply is illegal for Ubuntu to add this functionality in the United States under the current laws. The refresh rate issue does work correctly with certain monitors, but not as well with others. It is not an issue that will ever be 100% fixed for every single monitor (just like in Windows; you often have to install a monitor driver), but it might improve so that the ranges are automatically detected more correctly. Usually the automatic detection is pretty good.

---

### Post by adamkane on 2006-11-21
Right said. Ubuntu doesn't offer standard DVD playability, This is the biggest stumbling block to acceptance of Ubuntu.

---

