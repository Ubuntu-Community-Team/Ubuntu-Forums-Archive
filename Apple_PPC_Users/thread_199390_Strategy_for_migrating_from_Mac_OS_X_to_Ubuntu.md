---
title: "Strategy for migrating from Mac OS X to Ubuntu"
date: 2006-06-18
forum: Apple PPC Users
---

### Post by Christiaan on 2006-06-18
At some point in the near future I may decide to start using Ubuntu as my main OS.

One thing I'd love to see is a migration tool similar to that in Mac OS X (called Migration Assistant) except that instead of helping to migrate from one version of Mac OS X to another it would help you migrate from Mac OS X to Ubuntu. Is there anything like this available? What about for Windows users?

In the absence of such a tool what strategies have people been employing to migrate from Mac OS X to Ubuntu, and what are the potential pitfalls?

---

### Post by aysiu on 2006-06-18
I don't think there's a migration assistant from OS X to Ubuntu, but then again... I didn't think there was a migration assistant from Windows, either, and there turned out to be one, but I can't recall the link for it.

I don't think a migration tool is necessary, to tell you the truth. Mac OS X follows a very *nix-like structure, and it even uses *sudo* (same security model Ubuntu uses).

What exactly do you need migrated? I'm just curious.

---

### Post by projectle on 2006-06-18
Does one really need a "Migration Assistant" between any OS?

I mean, all you need to do is copy your Home Directory from OS X into Linux. Problem solved.

---

### Post by aysiu on 2006-06-18
Well, most of those files in the Home directory would be useless, anyway. *com.apple.plist* means nothing in Ubuntu.

Copying regular documents (music, Word, pictures, etc.) would be a simple copy and paste.

The only thing that might be difficult would be migrating Safari and Mail settings, assuming the person wasn't already using Thunderbird and Firefox in OS X, anyway.

---

### Post by hotani on 2006-06-19
I'm making the move shortly and haven't planned to do anything more than just dump my home directory onto the new system and transfer docs over.

---

### Post by Christiaan on 2006-06-19
> Does one really need a "Migration Assistant" between any OS? ... I mean, all you need to do is copy your Home Directory from OS X into Linux. Problem solved.

Well there's a little more to it than the home directory, but, in any case, the people I have in mind are not those who enjoy absolute control over and tinkering with their machines. The people I have in mind are the likes of myself and my father; people who aren't interested in doing things with their computers that could be automated instead.

> I don't think a migration tool is necessary, to tell you the truth. ... What exactly do you need migrated?

It's not a matter of necessity, it's a matter of usability and convenience (not something I've found GNU/Linux users to be generally interested in to be honest).

Ultimately I'd want to migrate user accounts, network settings, machine settings (date and time, display resolution, etc.), files (including web bookmarks, email, calendar and address book) and volumes. And I'd want to do this preferably by plugging in a firewire or USB 2 cable and clicking the mouse a half dozen times at the most.

Since there's no migration software to do it for me I guess my next question is how do I migrate data such as web bookmarks, email, calendar and address book (all from Apple's default software)?

---

### Post by swartzfeger on 2006-06-19
[QUOTE=Christiaan]Since there's no migration software to do it for me I guess my next question is how do I migrate data such as web bookmarks, email, calendar and address book (all from Apple's default software)?[/QUOTE]

What Mac apps do you currently use now?

For instance, if you use Firefox for OS X, it should be a simple matter of copying your bookmarks file to your Linux partition and import.

If you use Mail in OS X, you may want to install Thunderbird in OS X, import Mail into Thunderbird, then export your Thunderbird OS X mail into a file that Thunderbird for Ubuntu can import (in other words, I don't know if Linux apps like Thunderbird, Kmail etc can directly import from OS X's Mail format).

As far as iCal, Address Book and other apps, I don't know if their data is stored in an open or easily importable file format.

---

### Post by BoneKracker on 2006-06-20
I see it as a good opportunity for spring cleaning and prefer to do it myself (only I know what I need and want to keep).

One other idea: If you've been using Firefox, you can install the new browser sync plugin (from Google), and that will transfer all your bookmarks and whatever else you want (cookies, saved passwords, etc.).

Dual-booting for a while is a good strategy.  Even after you've transferred all your stuff, you can leave it there for a few months as the "non-default" OS in case you forgot something.  (I butchered 10 Gigs of music and had to go back and get it from an old iTunes database I happened to still have.)

---

### Post by alanphil on 2006-06-20
>As far as iCal, Address Book and other apps, 
>I don't know if their data is stored in an open 
>or easily importable file format.

1. OS X > Address Book > export entire database in vcard format
2. Ubuntu > Evolution > Contacts > select File, import 
3. Import the vcard file saved in step 1.

The Evolution Calendar also allows import of an iCal file, but I have not tried that to see if it works or not.

---

