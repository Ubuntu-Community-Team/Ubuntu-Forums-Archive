---
title: "Nvidia FX 5200 Driver Issues"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by pucenavel on 2008-01-16
Dear God, help me!

I am a newbie.

I have just finished installing 7.10.  After getting it up and running (actually installed 6.10), got my LAN connection working, upgraded to 7.4 & then 7.10.  After the 7.10 update, the system seemed to recognize the video card and showed me a restricted driver, which I acitvated.

The next order of business is to be able to see the whole screen at larger than 800x600 resolution.  Until I do that, I really don't want to proceed any further.

Although the driver seems to be there, it doesn't appear as a choice in the Screens and Graphics settings.  I've looked at other postings, but can't find the right combination of things to do that will make this work.

Any help would be appreciated.

---

### Post by Hospadar on 2008-01-16
Hullo! first off, if you havn't done anything really with your system yet, I would suggest you install 7.10 right off the bat (as opposed to doing the upgrading business).  you'll get a cleaner system and a more reliable installation.

Second, to get your drivers installed, go to System->Administration->Restricted Drivers Manager and enable it from there.

Third, if you still don't get more resolution choices, go to Applications->Accessories->Terminal and type (without quotes) "sudo dpkg-reconfigure xserver-xorg" on the first page, if you successfully installed the drivers from the restricted driver manager, be sure to select "nvidia" otherwise select "nv" (use spacebar to make selections) then you can just choose the default for most of the rest of the pages, and you'll come to a page with resolutions on it, use spacebar to select the resolution you want, and continue with the default choices after that.

Restart your machine, and now you should be able to get the choices you want.

P.S. if you don't know, resolution is normally changed by going to System->Preferences->Screen Resolution

If you get troubles installing the drivers or anything else, holler here with any sort of error messages you might get and we can try to sort things out.

---

### Post by pucenavel on 2008-01-16
That seemed to work.  I am now at 1024x768 (the highest my old Piece of S will handle).

Thank you!

---

### Post by pucenavel on 2008-01-17
OK, so I'm new at this & fully classify as "newbie", but that doesn't mean I can't contribute, right?

I did some learnin' after Hospadar helped me out (and as this is my first posting, I will stick to a personal commitment to follow up on the results after each time I reach out for help to fill in what I learned as a result -- as a newbie, I find it highly beneficial that there are people out there to help me fix things, but I really need to backtrack to find out just what the *&$# I did, otherwise I'll spend the rest of my days having others fix my problems - hopefully, this re-cap will help another newbie down the road).

Here is what I learned today -

***Disclaimer:  I may be wrong, mind you.  Like I said twice (or three times?) already, I am new at this***

Every file in the BASH has help built into it.  To see this help, type "man" followed by the command name.  (I'm reading Beginning Ubuntu Linux by Kier Thomas)

In this case, I typed

man dpkg-reconfigure

This gave me a breif explanation of what the command does (or already did, in my case).
Also useful is the use of info <commandname>.  These two both gave about the same information in this case, including;

 dpkg-reconfigure reconfigures packages after they have already been
       installed. Pass it the names of a package or packages to reconfigure.
       It will ask configuration questions, much like when the package was
       first installed.

BTW - both man and info provide WAY more information than using <commandname> --help.

Aha!  So, basically what I think Hospadar had me do was to force the system to reprocess the configuration that was set up automatically on my video, but this time doing it with some manual control.  Now that I know what I was doing, I feel much better.

A quick Google of the command name also provided a wealth of information, including a youtube recording of someone else actually doing exactly what I did!

---

