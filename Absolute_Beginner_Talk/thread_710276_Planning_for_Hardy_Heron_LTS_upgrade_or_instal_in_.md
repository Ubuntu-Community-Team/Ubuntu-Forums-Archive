---
title: "Planning for Hardy Heron LTS upgrade or instal in April"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by stig on 2008-02-28
This is a bit of advance planning. My wife and I have been using the Ubuntu 6.06 Long-Term Support (LTS) version on two networked PCs to run our home business. When the new Hardy Heron LTS version comes out in April I guess we will need to upgrade to it or do a fresh install. The question is what is the best way? I have read several advisories but still don't have a clear picture to suit my own situation.

Each of our PCs has two hard disks with the Home directory on one disk and the OS on the other. When Hardy Heron comes out I could upgrade in the normal way from 6.06. But I've read that you can't go direct from 6.06 to a much later version - you have to go through installs of the intermediate versions, which seems a hassle and dangerous.

Or I could follow item 3 in the guide at the top of this forum page which says "Go for Clean install instead of upgrade". But does a "clean install" allow me to use my present Home directory with all its data files and configuration files for the applications? Or does it wipe out my present Home directory.

Or perhaps I could install Heron alongside 6.06, using the present Home directory, then when I have got familiar with it, delete 6.06. And is this feasible?

I've read that you can install and use several distros and/or versions all with the one same Home directory. But wouldn't this result in problems in the configuration files? Wouldn't the configuration files have to be different for different versions because they will surely operate in different ways?

Whatever approach I use I don't want to lose all the customization I've done over the last couple of years. Much of this is for doing my work and running my business and I can't afford to lose it. For example, I have done a lot of customization in software like OpenOffice My software is from the Ubuntu repos but I use Ubuntzilla for Firefox and Thunderbird.

---

### Post by spamzilla on 2008-02-28
I believe there is or will be a direct update path from 6.06 to 8.04. IMO its best for a clean install so you have a fresh system, but this is up to you. And yes, if you DO NOT format your /home partition when installing Ubuntu, your /home partition should still be there when you log into Hardy.

Remember, before you do anything. **BACKUP YOUR DATA!**

---

### Post by hyper_ch on 2008-02-28
Devs are working hard to make a direct upgrade. However depending on the amount you changed in your system and installed stuff I'd rather recommend a fresh install also.

---

### Post by PmDematagoda on 2008-02-28
Whatever decision you take, I just will say this; do not rush to upgrade to Ubuntu 8.04, this is because Ubuntu 6.06 still has one year of support left so that you will not be in trouble if a vulnerability is found on it. So if you are going to switch then do it patiently and when it is really necessary:).

---

### Post by cotcot on 2008-02-28
Depends on what you have installed. I normally do a clean install alongside the older version including a new /home because i have used other repositories than the ubuntu supported ones.Once installed I copy my files from the old version but keep the old version until the overnext new release. I do this at the moment that i plan a backup anyway. 

I you upgrade with non-supported repos it is recommended to unmark them before upgrade.

---

### Post by tgalati4 on 2008-02-28
Assuming you have a local network, I would get a newer machine (better processor, larger disk, more memory, etc) then install Hardy on that.  That would preserve your existing Dapper machines and when you have time, you can check out the features of Hardy.

Since the machines are on the network, you can share files and printers.  One-by-one, test your critical business forms to make sure you can edit and print them on Hardy.  After a few months, you will have Hardy set up the way you want.

I expect a flury of bug fixes after Hardy gets released, so it probably won't be until May until Hardy becomes stable.  Dapper has exhibited excellent stability for me, and that's not something  you want to give up.

After several months, you can decomission one of the Dapper machines, or turn it into a server, or keep it as a backup machine, or put Hardy on it.

As the cost of computer hardware becomes cheaper and business downtime is expensive, it makes sense to add a machine rather than convert an existing machine to maximize uptime.

---

### Post by Duck2006 on 2008-02-28
I to will be waiting till some time in may to install 8.04.

---

### Post by stig on 2008-02-29
Thanks for all that valuable information. Sorry for the late response but I was away from PCs for the rest of the day.

Taking advice from what you have said, I will not rush to install Hardy but wait until it gets properly sorted. It also raises the question of what benefits will I gain by upgrading to Hardy from Dapper? Will I notice much difference? My main uses are OpenOffice documents and spreadsheets, Firefox browser and Thunderbird email (I already use Ubuntuzilla's latest versions of these), Gimp for photo editing - and these are all for both office/business and home use.

---

### Post by hyper_ch on 2008-02-29
quite a few things were updated. OOo is now 2.3, then there's Firefox 3, TB 2.0 (not sure what the dapper version is)...

and also better 3d support and 3d-desktop.... and whole other bunch ;)

---

### Post by tgalati4 on 2008-02-29
For the home desktop user, quite a bit.  For the business user, perhaps not so much.  If Open Office is working will all of your business forms under Dapper, then you might not see a difference.  There are bugs fixes, newer hardware supported, easier installation, better GUI configurations, overall a better desktop installation and use experience.

For routine business use, if your printing works, if you can share files, if you can do all the things that you need to do under Dapper, then you might not see the improvements.  Gutsy and perhaps Hardy actually use more resources than Dapper, so can run slightly slower on older hardware.  When you get a newer machine, then you can appreciate the improvements in hardware speed as well as the overall desktop improvements.

To get newer versions of applications in Dapper, uncomment (remove the #) in your /etc/apt/sources.list for the backports repositories.  This will give you access to some of the newer versions of software that is available in Gutsy.  There is some risk with these backports, but they are generally well-tested.

If you update one application at a time and test it with your business processes, you can take advantage of some of the gutsy improvements without having to do a complete upgrade.  Do it on only one computer at a time so that if an application breaks, you have a backup Dapper machine to use.  You can roll back individual updates, but it requires some effort.

Some applications are improving (such as evince PDF viewer) but 3rd party applications (such as acroread 8) work better.  Acroread handles form fields, dual-sided printing, mark-ups, quotation marks, and font kerning better than evince--so it's critical for businesses that use PDF office forms.  I don't know if acroread 8 runs on Dapper, but I would use it over evince (2.20.1) because it handles several cases better, especially with specially-formatted business forms.

Using backports gives you a preview of several improved applications before Hardy is ready for production use.  The bottom line:  it's the applications where the work gets done.  The operating system must support both the hardware and the critical applications.  If Dapper currently supports your hardware, then focus on upgrading the applications.  When you run into a wall--some applications can't be upgraded without a complete OS upgrade, then it's time to move to Hardy.

---

### Post by stig on 2008-03-02
Thanks for all the comments. I definitely agree with the statement "The bottom line: it's the applications where the work gets done".

Some basic things, from my perspective, never seem to improve. For instance I have commented on two in my post at the top of this page recently:
[http://ubuntuforums.org/showthread.php?t=659294&page=2](http://ubuntuforums.org/showthread.php?t=659294&page=2)

In that thread someone asked "I'm not sure what to call this, but here goes, is there a way that we can add multiple "windows" within one window.  i.e. having sorta newspaper columns that interact with each other...."

and I replied:

"I assume by "interact" you mean that when one column of file names reaches the bottom of the window it "wraps" over to begin a second column and then a third column etc. This is one feature that I really miss from my Windows days. Why do Linux applications always seem to lack this very useful feature? I like Nautilus in a number of ways but this is one of two missing features that make Nautilus "unfinished" for me.

The other missing feature is being able to open dual windows, side-by-side. I have the XFE file manager installed for this purpose and like it. The only reason I don't use XFE all the time is that it seems stuck in a grey-blue mode and I can't get the Gnome colours. There is an option in the XFE Preferences for choosing Gnome but the only thing it seem to do on mine is change the title bar to brown!

But if Nautilus could do the column wrap and dual columns I would love it!"

---

