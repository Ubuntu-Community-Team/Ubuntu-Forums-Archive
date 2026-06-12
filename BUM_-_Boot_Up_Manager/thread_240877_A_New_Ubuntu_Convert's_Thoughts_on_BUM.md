---
title: "A New Ubuntu Convert's Thoughts on BUM"
date: 2006-08-21
forum: BUM - Boot Up Manager
---

### Post by funchords on 2006-08-21
BUM takes on the difficult job of crossing the gap between technical concepts and actions and non-technical users.

I consider myself a technical user, with much experience in Windows internal services but a shaky grasp on the linux ones.  I understand the runlevels.

My objective in using BUM today was to turn off services that I am not using.  And, after some trial and error, and visiting the BUM web site and reading the [documentation]("http://www.marzocca.net/linux/bumdocs.html#use"), I think I've figured that out.  But I wanted to take this opportunity to tell you about my experience.

What impressed me positively:
 - The opening screen (non-"Advanced") opens to a list of clear and useful descriptions.  The description of the behavior of the service boldly preceeds the cryptic name.  The descriptions strike a balance between human understandability and technical precision.
 - As a somewhat more technical user, the Advanced screen helped clear up some of the ambiguity I was experiencing.

What confused me:
 - The Activate/Deactivate terms confused me. I didn't know if I was starting/stopping a running service, or if I was selecting which services would or would not run on the next boot.  I expected clearer choices telling whether a service would be affected now, affected on the next boot, or both.
 - After applying a change to whether something was Activated or Deactivated, the status of the "Activate" checkmark did not change.  I had to quit the application and restart it to see that the change took place.
 - For any particular service, the choices in the Services menu item did not match the choices in the right-click menu.  The presentation in the Services menu was clearer to me.  It was helpful to see the greyed out choices as it gave me clues as to what I could expect to see should I change the current state of the service.  It gave me comfort that if I changed it and later decided to change it back, that I would be able to do so.
 - If I change some checkmarks on some services (without Applying), then right-click on a service and choose to "Activate & Apply Now," does that "Apply Now" work for all of the services I changed or just the selected service?
 - According to the documentation, a Question Mark in the running column either means "BUM is not able to detect if the script is running a daemon" or "BUM doesn't have a nicer description for the service and so it is showing the apt-cache description."  I have a question mark next to a few services. Is it the first meaning or the second meaning?

What I couln't find:
 - The Help menu item does not lead to help files or documentation.  The two choices are "About" and "Report a new service description."  I expected to find help like the help I eventually found in the [documentation]("http://www.marzocca.net/linux/bumdocs.html#use"). 
 - I looked for a "reload" or "refresh" button, but did not find it.  I wanted to see whether a service had recently started or stopped, or whether my changes had been applied.

Although I described a few things that slowed me down, **I am very impressed with Boot Up Manager. **  I think it's a great fit for Ubuntu!  If I was too overwhelmed by the techno-speak, or if it was simplified to the extent that it was too ambiguous, I would not have been encouraged to continue to use it.  I hope you find this feedback constructive and encouraging.

---

### Post by saltydog on 2006-09-11
Thank you Robb,

I will take in due consideration your suggestions.

> **funchords said:**
> 
 - The Activate/Deactivate terms confused me. I didn't know if I was starting/stopping a running service, or if I was selecting which services would or would not run on the next boot.  I expected clearer choices telling whether a service would be affected now, affected on the next boot, or both.


From the docs: "...Activate a de-activated script. When a service is activated, all symlinks in RL 2-3-4-5 are changed to
Sxx, where xx is..."

So activating a script just means that the script will have an entry in RL2 at next boot. To Start/Stop a service you need to right-click on it.

> 
 - After applying a change to whether something was Activated or Deactivated, the status of the "Activate" checkmark did not change.  I had to quit the application and restart it to see that the change took place.


No, in order to make activation/deactivation permanent, you just need to press on "Apply" button. 

> 
 - For any particular service, the choices in the Services menu item did not match the choices in the right-click menu.


I can't confirm this. Are you running latest v.2.1.7?

> 
 - According to the documentation, a Question Mark in the running column either means "BUM is not able to detect if the script is running a daemon" or "BUM doesn't have a nicer description for the service and so it is showing the apt-cache description."  I have a question mark next to a few services. Is it the first meaning or the second meaning?


From the docs:
"? BUM is not able to detect if the script is running a daemon"


Thanks again for cooperation,

Fabio

---

### Post by yabbadabbadont on 2006-09-14
> No, in order to make activation/deactivation permanent, you just need to press on "Apply" button.
Having just purged bum from my system because the program did not appear to do what I told it to do, let me respectfully disagree with you.  Pressing the "Apply" button may make the changes requested, but doing so without exiting and re-entering the program only refreshed the display with every service checked again.  Now that I've read the post previous to yours, I'll reinstall the program and verify that it actually works.  I've been using linux since Slackware '96 and am quite comfortable with editing the runlevel links directly.  However, I've read in the forums and on the wiki that BUM is the preferred method for doing so (in Ubuntu) and thought that I would try it out.  Please update the program so that when the "Apply" button is pressed, the display refreshes with the real status of the various services displayed.

---

### Post by saltydog on 2006-09-14
> **yabbadabbadont said:**
> Having just purged bum from my system because the program did not appear to do what I told it to do, let me respectfully disagree with you.  Pressing the "Apply" button may make the changes requested, but doing so without exiting and re-entering the program only refreshed the display with every service checked again. 

You're right. This wasn't fixed as I didn't realized, and no debian bug has been opened on that.

Anyway, now it is fixed in svn and soon in debian main (few days)

Thanks for cooperation.

Fabio

---

