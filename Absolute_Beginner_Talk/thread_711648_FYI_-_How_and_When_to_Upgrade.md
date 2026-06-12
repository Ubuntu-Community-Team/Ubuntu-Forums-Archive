---
title: "FYI - How and When to Upgrade"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by bsmith1051 on 2008-02-29
(the following is a reworked version of the post I originally made back in Nov '07 in the "Installation/Upgrades" forum and, at the time, just as a suggestion.  No one replied but I still think it's a really good idea...)
________________

**HOW AND WHEN TO UPGRADE YOUR UBUNTU SETUP**

'Straight' talk about upgrading Ubuntu, presented in 7 parts.

**1) What's the purpose of this FAQ?**

- I am assuming that you have already installed Ubuntu and so this FAQ does not have any discussion of actual procedures.
- Not focusing on specific versions allows this FAQ to stay applicable across all versions.
- My impression is that 'a lot' of people regret upgrading their Ubuntu systems.  This mostly seems to happen because people assume that upgrades work 100% of the time, and that all their existing programs and customizations will continue to work; they don't.
- I'm totally open to suggestions for this FAQ but I also want to limit it's size so I'll only update the original post with really key info.  In particular I'm trying to follow the 'At most 7 items' rule for keeping things simple.

**2) Why should I upgrade?**

- Each new release of Ubuntu includes new and improved versions of the various software programs.  Some of these new versions are also available for previous Ubuntu releases, but if there's something important to you which is not 'back ported', e.g. newer OpenOffice, then it's probably time to upgrade your entire Ubuntu setup.
- The automated upgrade process (described below) is only tested for the version of Ubuntu immediately prior, i.e., you can't wait for more than 1 new version to come out and then try to upgrade through 2 or more updates.
- Every version of Ubuntu will eventually stop receiving security updates -- from initial release, 36 months for Long Term Support/LTS versions, 18 for interim versions

**3) Why wouldn't I upgrade?**

- If you're happy with your current setup, just let it ride.  You'll continue to receive updates for at least a little while (see comment above re security updates)
- If you've heavily customized your setup, then an upgrade is probably going to cause more problems then improvements.  Besides, you're probably an advanced user who doesn't need this FAQ anyway!
- Unfortunately, there's no such thing as a perfect 100% guaranteed upgrade.  There are just too many variables.  The less you've customized your current install, however, the more likely it is to succeed. 
- Finally, you might want to simply delay upgrading until your 3rd-party apps have been updated to work on the new version.  For instance, if you've been installing any app that comes in per-version downloads (e.g. VirtualBox for Feisty vs VirtualBox for Gutsy) then you should probably wait until they release a version for the new Hardy.

**4) What's the easiest way to upgrade?**

- The easiest way to upgrade is simply to load the Update Manager, select "Install new version" and hope for the best.  The vast majority of the time, this will work just fine.  And if you've done nothing to customize your setup, it's almost guaranteed to work.  But hopefully you'll have the time and energy to do a little CYA first (see below).
- In the following sections I suggest two alternate ways to upgrade -- the Ideal, and the Reasonable, plans

**5) What's the ideal way to upgrade?**

- Ideally you would never upgrade -- you'd do a clean install instead. But this takes a lot longer and is more complicated to do.
- You would also, ideally, want to use a new hard-drive each time.  This has several benefits: 
[LIST]you can easily switch back to your original setup since the original drive would be untouched
[*]you can mount the old drive as a secondary/data drive and copy your old data and/or settings as needed
[*]you can take your original drive and store it, i.e., if you're a typical computer-owner and never make backups
[*]hard drives are by far the _least_ reliable part of your computer, so it's good to proactively replace them![/LIST]
- By doing a clean install, you'll lose all your custom settings.  But afterwards you can selectively restore your original home directory files, i.e., the hidden configuration folders, and watch to see if the new versions of each program 'accept' the old configuration files (and hopefully upgrade them)
- Finally, ideally you've been making notes of everything you've customized; I know **I do** but then I've worked in IT for 20 years and have learned the hard way to be ultra-organized.  After a clean install you could then manually re-apply the customizations you still want.

**6) What's a reasonable way to upgrade, a way without too much extra work?**

[LIST=1]Make sure you have access to another computer with Internet access, so that you can reach these support forums for research and help.
[*]Make a backup of your personal files beforehand.  By default, this would be the entire /home/<you> folder but if you've been storing files in other folders then you should know where they are, too!
[*]Undo any custom configuration, e.g. proprietary video drivers.
[*]Try booting with the new LiveCD for the new version.  Make sure that the network card is detected.  Look for any other hardware detection problems?
[*]Use the Update Manager to do an online update.  But don't do it right after a new version comes out!  If you wait a week or two, you'll avoid the initial rush which can cause the online servers to overload or stall (and mess up your upgrade?).  Also, the longer you wait, the more additional bug fixes will be included (updates which the CDs wouldn't have). P.S. I've tested this and it's true -- the online update always downloads the latest versions of everything.  (You might also be able to update using the Alternate CD which includes the option to download updates before installing.)
[*]Keep a list of the recovery tips (below) handy.[/LIST]

**7) How do I recover from a botched upgrade???**

- If your computer restarts but goes to a command-line rather than the GUI, login and re-run the video setup,
```
 > sudo dpkg-reconfigure xserver-xorg
```
- If your computer refuses to load Ubuntu, boot the LiveCD and see if you can access your files.  (You _do_ have a LiveCD from my previous suggestion re testing the network driver beforehand, right?)  This will tell you if there's been a hard drive failure.  It will also allow you to correct the configuration file(s) causing the problem.

---

### Post by SOULRiDER on 2008-02-29
Looks interesting, why dont you ask a mod to move it tot he Tutorials and Tips forum?

---

### Post by dcstar on 2008-03-01
> **SOULRiDER said:**
> Looks interesting, why dont you ask a mod to move it tot he Tutorials and Tips forum?

Because too many people would laugh at the instruction to use a brand new hard drive for every upgrade?

Ubuntu releases a new version every 6 months, it is not realistic - or anywhere near justified - to expect people to purchase new hardware on this schedule.

There are also (in every new Ubuntu version I have seen) "official" instructions in these forums on how to upgrade to the new version, and to have additional instructions serves little purpose other than to confuse some users who invariably stumble over these posts instead of ones that are more appropriate.

HOWTOs and other instructions have value when they are filling a void, but when too many things exist trying to achieve the same aim them at some point they become counter-productive.

The "Tutorial and Tips " forum exists for these things, and it is moderated so it is not filled up with good intentioned (but ultimately counter-productive) posts.

---

### Post by bsmith1051 on 2008-03-01
I agree that there are too many FAQs already.  But I don't think any of the suggestions I make here are clearly stated anywhere else.  I originally (back in Nov '07) suggested that some of these things be added to the 'official' FAQs in the Install/Upgrade forum but no one responded.   And have you _tried_ to read the FAQs in these forums?  They have maybe a paragraph or 3 of good information followed by lots of outdated information, followed by lots of unrelated discussion.  How many times have I had to reset my xserver settings, just from 'normal' updates breaking it, and every time I have to search and search until I find the right keyword to find the needed command.  I'd love to see a moderated FAQ for "Common problems" ?

re new drives, I thought I was pretty clear that using a new hard drive is 'Ideal' (as opposed to 'Reasonable') and, frankly, I do replace my hard drive every 6-12 months.

Finally, as I also stated up-front, I was trying to list general advice not specific to any particular version.  So the fact that each new version includes official instructions is immaterial.  Those instructions don't include 'philosophic' discussion like in this FAQ.

---

### Post by alecspoons on 2008-03-02
The hard drive suggestion aside (and I got what you meant), I thought I'd say that I found this useful to read. As a newbie to Ubuntu, I found this post answered the exact questions I came searching for.

I'm loving Ubuntu and there's no question of my returning to Windows. But I've never been through an upgrade to a new version of Ubuntu and this told me just what I wanted to know.

Thanks bsmith1051 - I found it helpful.

---

### Post by bsmith1051 on 2008-03-02
> **alecspoons said:**
> Thanks bsmith1051 - I found it helpful.
Sweet! :guitar:

---

### Post by bsmith1051 on 2008-03-06
FYI - Updated the original post to mention the possibility of 3rd-party apps (e.g. Virtualbox) not being immediately compatible with the new upgrade, and also mentioned the possibility of upgrading with the Alternate CD which includes the option to download new updates before installing.

---

### Post by cyphgas on 2008-03-08
yup, this was helpful, i always forget the xserver command.
thanks

---

