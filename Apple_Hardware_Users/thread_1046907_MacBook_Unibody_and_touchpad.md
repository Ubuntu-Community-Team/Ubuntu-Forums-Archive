---
title: "MacBook Unibody and touchpad"
date: 2009-01-21
forum: Apple Hardware Users
---

### Post by bobcopro on 2009-01-21
I want to thank everyone here for their dedication to all the hard work in making Ubuntu work on the new MacBooks.  I have 25 years PC service experience and recently bailed to a Mac, then to Ubuntu so I'm new to both.  

I got the basics down doing Ubuntu on two OLPC laptops, then takled the new Apple.  There are a lot of threads out there on triple booting and most don't work.  I did finally find one that did, got it going and tried following different directions for getting the new MacBook running.  A lot of threads have no dates and no reference to which model MacBook.  I finally trashed the Ubuntu install and started over using this thread [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) and it worked wonderfully.  

The purpose of my post is that unlike many, I really like the tap feature of the new touchpad,,,, - not having to push down to click.  I couldn't find the documentation anywhere to alter the new /etc/hal/fdi/policy/appletouch.fdi file to make that work, so I started playing with it.  For all the other lost folks out there change the three lines:

        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>

to match the click finder line as below:

        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>

I need to play with some of the other sensitivity settings to my preferences, but this little detail makes me very happy.  If this information is elsewhere feel free to delete this post, but I couldn't find it.

Now off to get some control over the lighting and power consumption, maybe even some sound.  Final note - I noticed the guide I used above is like so many with no obvious reference as to when it was last updated, so it's hard to know if this is current when you are searching all over.  Perhaps a thought for all future "How To" pages.  Thanks all again for all the help.  I'll post some more numbers from the touchpad file as I find them

---

### Post by cyberdork33 on 2009-01-22
You found a documentation page in the wiki. They are updated continuously. We recently moved to a new naming scheme and you seem to have found the old page that was in transition... Here is the starting point for any Mac user wanting to install Ubuntu:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

and the various ways to dual / triple boot are covered here:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

a listing of all the synaptics settings that you can set for your touchpad are in the man page for synaptics. type 'man synaptics' in a terminal to browse. Note that it assumes you are adding options to your xorg.conf which is really an older style of doing things. You will need to put them in the XML format you have been using. Good Luck.

---

### Post by topdrawersausage on 2009-02-20
many thanks for posting this bobcopro, that's exactly the thing that's been bugging me too :D

---

