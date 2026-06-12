---
title: "Questions on a dual boot with Windows XP"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by crystal on 2006-06-30
I am currently primarily using Windows XP, but intend to switch to a Windows XP + Ubuntu Linux dual boot setup. After reading a tutorial on [Partitioning Windows and Ubuntu](http://psychocats.net/ubuntu/partitioning.html), I learnt of an [Ext2 Installable File System For Windows](http://www.fs-driver.org). As such, I plan to have an NTFS partition for Windows, an Ext3 partition for /home where the shared data would be, and another Ext3 partition for Ubuntu (and a swap partition, of course).

One thing I want to confirm is migration of data. I can simply save my textfiles, PDFs, mp3 files etc to CD, and then copy back after the installation, right? In particular, I use Firefox and Thunderbird on Windows. Would simply copying the respective profiles work? I dont see a problem for the bookmarks in Firefox, but I do want my mail in Thunderbird to be accessible and uncorrupted under Ubuntu.

Using the Ext2 installable file system for Windows, is it possible for me to have Firefox on Windows use the same profile as Firefox on Ubuntu? I may still want to browse the Web on Windows, and in the course of doing so may change settings (e.g., add a bookmark) that I want to have reflected in Ubuntu.

Now, I intend to do some development work in C++. It would be useful to be able to easily develop and test programs under both Linux and Windows. Is it feasible to have a [Subversion](http://subversion.tigris.org) repository in the shared data partition? I reason that at worst it should be no different from accessing a remote repository, but I should be able to access it as a local repository.

Thanks for any help rendered :)

---

### Post by Ctrl+Alt+Del on 2006-06-30
afaik the ext2 driver works just as well with ext3, but it's been a while since i used it, hence no need to stick to a non-journaled fs.
you can simply copy your data back, only culprit there is the windows<-> unix text conversion for plain text files, but any smart txt editor should be able to handle that.
As for the profiles. I went with a bookmark synchronizer extension for firefox and have my mail on imap servers, so that's not much of a problem for me. But i see no reason as to why shared profiles should not work.
About svn: no clue sorry ;)

---

### Post by Xzallion on 2006-06-30
Copying your data to a cd and returning works just fine.  No worries there.
For firefox there are extensions to create a back up of everything, like all your extensions, your bookmarks etc.  A quick search on their extension site should help, but I can't vouch for just copying the profiles from Firefox.

Edit:  Heres the [backup extension]("https://addons.mozilla.org/firefox/2109/").

You can't have the same profile, but theres a extension that lets you sync your firefox bookmarks across multiple computers.  I use it to keep my windows/ubuntu firefox bookmarks identical.

Edit:  Heres one of many [backup extensions]("https://addons.mozilla.org/firefox/2410/").  More can be found by going [here]("https://addons.mozilla.org/firefox/extensions/") and searching for "synchronize".

I have no experience with subversion so I can't really help you there.

---

### Post by crystal on 2006-06-30
> you can simply copy your data back, only culprit there is the windows<-> unix text conversion for plain text files, but any smart txt editor should be able to handle that.
Thanks, I agree that the new line sequences should be handled well by the text editor.

> You can't have the same profile, but theres a extension that lets you sync your firefox bookmarks across multiple computers. I use it to keep my windows/ubuntu firefox bookmarks identical.
Okay, does that mean that the profile format is different between Linux and Windows? If it was it same, I thought one might be able to just change the profile location in say the Windows version of Firefox to point to the profile of the Linux version. Thanks again :)

---

### Post by Xzallion on 2006-06-30
It might be the same, I just don't know.  I would say give a try and find out ;)

---

### Post by crystal on 2006-06-30
Ah, I think the Firefox/Thunderbird profile question is actually answered by [Howto Thunderbird/Firefox profile share XP & Dapper](http://ubuntuforums.org/showthread.php?t=203524). It is written for a FAT32 shared partition, but it looks like it should work for an Ext3 shared partition with the Ext2 filesystem for Windows.

I suppose for Subversion I will just have to give it a try.

Thanks again, Ctrl+Alt+Del and Xzallion.

---

