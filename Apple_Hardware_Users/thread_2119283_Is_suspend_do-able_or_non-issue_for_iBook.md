---
title: "Is suspend do-able or non-issue for iBook?"
date: 2013-02-23
forum: Apple Hardware Users
---

### Post by este.el.paz on 2013-02-23
Gents, etc:

I've recently posted a few questions asking about suspend in Lu 12.04 for iBook G4 with Radeon GPU and no direct answers have been provided, so I'm asking again.  The LiveDVD of Lu 12.04 doesn't have a "suspend" button or if it does, doesn't "suspend" . . . googling my question today I saw from about a year ago posts saying that "suspend doesn't work" . . . .  Has that changed in the ensuing passage of time and Lu development? 

Another posted suggested that Xubuntu 12.04 would provide suspend . . . and then another talking about how closing the clamshell in Lu didn't put the machine into suspend or it wouldn't wake up from it when the lid was opened.  The last suggestion reminded me that this time I didn't remember to actually close the lid to check that, I just checked for "suspend," based upon my iMac experiences, needing to reboot into and out of Xu/Lu each time I wanted to put the computer to sleep . . . and it didn't work in the iBook.  So, when I get a chance to get back to my iBook, I'll check that, certainly if it sleeps when the lid is closed and then wakes, that is OK; I do recall one system I checked awhile back in the Xu/Lu /Ku series where closing the lid, just closed the lid and the computer was still "awake" . . . thinking and stuff, under the closed lid.

So, question--can Lu 12.04 be persuaded to "suspend"? . . . let's say I don't want to close the lid, but just want to put the unit to sleep with the lid up.  Or, will the laptop go to sleep if I close the lid and then wake when I open it?  Testing with LiveDVD did not provide "suspend"--would the installed version be different or fixable?

And/or--Would installing Xu 12.04 provide suspend and then I could install the LXDE DE and that would give me LTS and lightweight DE . . .???

Thanks,

e.e.p.

---

### Post by danield on 2013-02-25
The terminal command to suspend is pm-suspend.  I'm using Openbox, so I just put that command into a new menu item.  I don't have 12.04, but in my experience some installs have a working suspend, some don't.  Usually it's a new kernel that breaks it, I think.  Also, KMS does not support suspend on PowerPC, so if you enabled KMS by disabling the radeon framebuffer in order to get 3D acceleration, suspend will break.  I'm not sure if that pertains to 12.04 or just 12.10.

---

### Post by este.el.paz on 2013-02-25
> danield 	 		**Re: Is suspend do-able or non-issue for iBook?**
 		The terminal command to suspend is pm-suspend.  I'm using Openbox, so I  just put that command into a new menu item.  I don't have 12.04, but in  my experience some installs have a working suspend, some don't.   Usually it's a new kernel that breaks it, I think.  Also, KMS does not  support suspend on PowerPC, so if you enabled KMS by disabling the  radeon framebuffer in order to get 3D acceleration, suspend will break.   I'm not sure if that pertains to 12.04 or just 12.10. 	

@danield:

Thanks for taking the time to reply and suggestion for using terminal command to get suspend to work, perhaps I could try that with the LiveDVD.  So far I haven't installed the Lu system, but haven't done anything to get 3-D acceleration.  I see that the 12.10 system looks a little more complicated to get going on PPC stuff??

Anyway, since I posted this question rsavage has posted on the "Testers wanted for 12.04" thread that he will be setting up a Xubuntu 12.04 iso, hopefully as LiveDVD, with the intent to have suspend work from the GUI . . . .  I am looking forward to that as the probable solution for me . . . .

e.e.p.

---

