---
title: "LiveCD (6.06) fail to load"
date: 2008-06-24
forum: Apple Hardware Users
---

### Post by HydroxyMethylRadical on 2008-06-24
When trying to load iMac G5 with Desktop CD (6.06) it sucessfuly passes up to KDE loading but hangs when KDE is "detecting peripherials" (as indicated on the splashscreen). What can i try to make it start or if there any way to stop KDE from loading and get console.

---

### Post by stream303 on 2008-06-24
For a G5 iMac, try using the latest Hardy 8.04 instead.  The reason is that thermal fan-control in Dapper was not available, and your fans will absolutely scream.

This problem was fixed in post-Edgy I believe.

Note that on my rev-a, no als model with 20" screen using nv video, there is a slight bug with the display shifting about a half-inch to the right.  Awaiting fix from freedesktop.org.

If you have this model, and the video bugs you, you can drop back to either Feisty 7.04, or Gutsy using the Feisty video driver.

The fan issue in Dapper for the G5 iMac is a showstopper, so that's why I'd recommend getting Hardy 8.04 and trying that instead - IF you can live with the small video bug that shifts to the right just a bit.  If you are running a small amount of ram and still want to install, try the "alternate" installer.  Note that the fans will scream while installing, but will calm down on the first reboot with these later releases.

So currently, the most bug-free version out of the box for a 20" G5 iMac with nvidia is Feisty, 7.04.

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by HydroxyMethylRadical on 2008-07-04
Thanks a lot - it works. 

PS You're right the fan scream was real hell :)

---

