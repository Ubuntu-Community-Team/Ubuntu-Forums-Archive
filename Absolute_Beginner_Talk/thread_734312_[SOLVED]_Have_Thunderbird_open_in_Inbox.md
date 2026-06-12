---
title: "[SOLVED] Have Thunderbird open in Inbox"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Bruce M. on 2008-03-24
Hi Folks,

I have posted this at the T-Bird Support site as well.

I'm using T-Bird version 2.0.0.12 (20080227) - Xubuntu 7.10

I saw this at the T-Bird support site:
If you want Thunderbird to open directly in your Inbox when you launch the application, go to "Tools -> Account Settings -> Server Settings" and check the box that says "Check for new messages at startup."

In my T-Bird **Account Settings** isn't under Tools. It is under Edit > Account Settings
I have:

(*) Check for new messages at start up
( ) Check for new message every [10] minutes
(*) Automatically download new messages

T-Bird never starts in my Inbox
**It always starts in *Local Folders*** (even when new messages appear)

At times I see: Getting 2 of 5,  and Inbox is BOLD with (1) beside it, but T-Bird stays at Local Folders.

How can I get it to start in Inbox?
Anyone here know how?

Bruce

---

### Post by kellemes on 2008-03-24
For some reason it works at my end, I just forgot how I did it..
Maybe you need the following extension?
[http://www.varesano.net/blog/fabio/thunderbird+sort+rearrange+accounts+and+define+startup+folder+using+folderpane+tools+exte]("http://www.varesano.net/blog/fabio/thunderbird+sort+rearrange+accounts+and+define+startup+folder+using+folderpane+tools+exte")

---

### Post by Bruce M. on 2008-03-24
> **kellemes said:**
> For some reason it works at my end, I just forgot how I did it..
Maybe you need the following extension?
[http://www.varesano.net/blog/fabio/thunderbird+sort+rearrange+accounts+and+define+startup+folder+using+folderpane+tools+exte]("http://www.varesano.net/blog/fabio/thunderbird+sort+rearrange+accounts+and+define+startup+folder+using+folderpane+tools+exte")

Interesting idea, but I only have one mail account and T-Bird should start in the Inbox by default if I have the correct settings (this comes from their Support Page). However if I can't get T-Bird to do what it should do naturally, this might become an option as a last resort.

Thanks for the link.
Bruce

---

### Post by forrestcupp on 2008-03-24
In mine, it just opens up in the last folder I was using when I closed it.  So if I click on the Inbox and close it, it will open to the Inbox.

---

### Post by drs305 on 2008-03-24
I am using Swiftdove and have the same issue as the OP. I have tried ensuring the server checks mail on startup, uninstalling all add-ons, changing the default email account, having only one server check for email on startup, etc. I've also tried differing views (normal, wide, message pane, today pane) but none make a difference. The inbox is still not displayed on opening although I am sure that it did until recently.

---

### Post by Bruce M. on 2008-03-24
People, people ....

Other than kellemes no one has even tried to answer the question which is:

**[CENTER]How can I get Thunderbird, not Swiftdove, to open in Inbox?[/CENTER]**

Thank you
Bruce

---

### Post by FreewareFan on 2008-03-24
Check this setting:

Edit - Account Settings - Server Settings - Advanced -  Then check to see that the box beside 'Inbox for this servers account' is checked..  

That might solve your issue.

---

### Post by forrestcupp on 2008-03-24
> **Bruce M. said:**
> 
**[CENTER]How can I get Thunderbird, not Swiftdove, to open in Inbox?[/CENTER]**

Thank you
Bruce

Well, I was talking about Thunderbird.  If what I said doesn't work for you, that's strange.

Also, Swiftdove *is* Thunderbird.  It's just been compiled in an optimized fashion.

---

### Post by sillyxone on 2008-03-24
what version of Thunderbird are you using? can you try to set it back to default settings (rename ~/.mozilla-thunderbird to something else and let it create again) and try again to see what the default behavior is.

the reason I'm asking this is that I spent the last 10 minutes playing with my Thunderbird and I could NOT set it to anything else than Inbox (it doesn't remember last selected folder neither). If you want more settings, go to Edit -> Preferences -> Advanced -> Config Editor.

---

### Post by Bubba64 on 2008-03-24
> **kellemes said:**
> For some reason it works at my end, I just forgot how I did it..
Maybe you need the following extension?
[http://www.varesano.net/blog/fabio/thunderbird+sort+rearrange+accounts+and+define+startup+folder+using+folderpane+tools+exte]("http://www.varesano.net/blog/fabio/thunderbird+sort+rearrange+accounts+and+define+startup+folder+using+folderpane+tools+exte")


Thanks to Bruce M for bringing up this point and kellemes for providing a working answer I followed the link and down loaded the add on then opened it in Thunderbird and it works, I also use all tray to have Thunderbird at one click fast access and to have easy notification of incoming mail.

---

### Post by forrestcupp on 2008-03-24
> **sillyxone said:**
> what version of Thunderbird are you using? can you try to set it back to default settings (rename ~/.mozilla-thunderbird to something else and let it create again) and try again to see what the default behavior is.
If you do that, you'll lose all of your emails, account settings, and contacts.

---

### Post by sillyxone on 2008-03-24
> **forrestcupp said:**
> If you do that, you'll lose all of your emails, account settings, and contacts.

I'm pretty sure it won't do that. You can always restore the old folder to overwrite the newly created folder.

I'm saying this because I have the mozilla-thunderbird folder stored in an encrypted place. If I start thunderbird without mounting the encyprted folder, it just start with some blank settings. But as soon as I mount the encrypted folder over ~/.mozilla-thunderbird, I can access my normal account as usual.

---

### Post by drs305 on 2008-03-24
> **Bruce M. said:**
> People, people ....

Other than kellemes no one has even tried to answer the question which is:

**[CENTER]How can I get Thunderbird, not Swiftdove, to open in Inbox?[/CENTER]**
Bruce

Bruce,

I wasn't trying to hijack your thread. Swiftdove is pretty much an optimized version of Thunderbird.  Everything I listed was what I tried after reading your post to get it to open with the Inbox selected (with no success). I was just trying to eliminate some of the other possibilities and hoped I'd stumble across a solution for both of us.

Cheers.

---

### Post by forrestcupp on 2008-03-25
Well, here's something you can try.  Go to Edit->Preferences and click the Advanced tab.  Go to the General tab in the advanced settings and make sure the box next to 'Remember the last selected message' is checked.  Mine was checked, so maybe that's why mine works like I described earlier.

---

### Post by Bruce M. on 2008-03-25
> **kellemes said:**
> For some reason it works at my end, I just forgot how I did it..
Maybe you need the following extension?
[http://www.varesano.net/blog/fabio/thunderbird+sort+rearrange+accounts+and+define+startup+folder+using+folderpane+tools+exte]("http://www.varesano.net/blog/fabio/thunderbird+sort+rearrange+accounts+and+define+startup+folder+using+folderpane+tools+exte")

Ok, I have this now.  Have it set up to open "Inbox on Local Folders". As you see in the attachment is opens on **Local Folders** {sigh}

> **FreewareFan said:**
> Check this setting:

Edit - Account Settings - Server Settings - Advanced -  Then check to see that the box beside 'Inbox for this servers account' is checked..  

That might solve your issue.

When I do that I see a thousand folders/files like:

127.0.1.1:+21688
abook.mab
blocklist.xml
etc etc

{sigh}

> **Bubba64 said:**
> Thanks to Bruce M for bringing up this point and kellemes for providing a working answer I followed the link and down loaded the add on then opened it in Thunderbird and it works, I also use all tray to have Thunderbird at one click fast access and to have easy notification of incoming mail.

Glad it works for you.  :)

> **forrestcupp said:**
> Well, here's something you can try.  Go to Edit->Preferences and click the Advanced tab.  Go to the General tab in the advanced settings and make sure the box next to 'Remember the last selected message' is checked.  Mine was checked, so maybe that's why mine works like I described earlier.

Tried that, even clicked on a message in the "Inbox"
It opened in **Local Folders**

{sigh}

Beginning to think I'm really dumb here.  :(

---

### Post by kellemes on 2008-03-25
Indeed there is something strange going on..
My Folderpane Tools options dialogbox shows me all email-accounts in the list.
When I select "Overrride startup folder" and click the "select folder"-combobox I can select one of **all** the account-folders I want to start in.

Don't you get to open the combobox next to "select folder"? You should be getting a list of folders..

---

### Post by Bruce M. on 2008-03-25
> **kellemes said:**
> Indeed there is something strange going on..
My Folderpane Tools options dialogbox shows me all email-accounts in the list.
When I select "Overrride startup folder" and click the "select folder"-combobox I can select one of **all** the account-folders I want to start in.

Don't you get to open the combobox next to "select folder"? You should be getting a list of folders..

Yup, and I select "Inbox" and it still opens on "Local Folders"  :(

I wonder if it's an Xubuntu things?
At this point I am at a total loss and grabbing at straws. :confused:

---

### Post by drs305 on 2008-03-25
> **Bruce M. said:**
> Yup, and I select "Inbox" and it still opens on "Local Folders"  :(

I wonder if it's an Xubuntu things?
At this point I am at a total loss and grabbing at straws. :confused:

Nope. I run Swiftdove/Thunderbird in 64 bit ubuntu and the same thing is happening to me....

---

### Post by Bruce M. on 2008-03-26
Well, I'm not getting much help from the Thunderbird support sire either.

[Look here]("http://forums.mozillazine.org/viewtopic.php?p=3309274#3309274")

Oh well, I guess it's an "Un-documented feature"

But I'll leave this open just in case someone comes up with something.

Have a nice day folks.
Bruce

---

### Post by bimmerd00d on 2008-05-11
Open up the properties for your extension, and remove %u from the end of it.  This will cause t'bird to open in your default folder.  Dont know why, but it seems to do the trick.  Found it in the last post of this thread.

[http://ubuntuforums.org/showthread.php?t=715874&highlight=start+thunderbird+in+inbox+folder](http://ubuntuforums.org/showthread.php?t=715874&highlight=start+thunderbird+in+inbox+folder)

---

### Post by Bruce M. on 2008-05-11
> **bimmerd00d said:**
> Open up the properties for your extension, and remove %u from the end of it.  This will cause t'bird to open in your default folder.  Dont know why, but it seems to do the trick.  Found it in the last post of this thread.

[http://ubuntuforums.org/showthread.php?t=715874&highlight=start+thunderbird+in+inbox+folder](http://ubuntuforums.org/showthread.php?t=715874&highlight=start+thunderbird+in+inbox+folder)

YES!!!!!!! Like bimmerd00d, I don't know why, but it did work here too.

Colour me happy.
Thanks bimmerd00d

Have a nice day.
Bruce

---

### Post by korin43 on 2008-05-14
Another thing to do to fix this is to right click on the inbox folder and check "favorite folder".

---

### Post by DeMus on 2008-05-15
> **Bruce M. said:**
> Hi Folks,

I have posted this at the T-Bird Support site as well.

I'm using T-Bird version 2.0.0.12 (20080227) - Xubuntu 7.10

I saw this at the T-Bird support site:
If you want Thunderbird to open directly in your Inbox when you launch the application, go to "Tools -> Account Settings -> Server Settings" and check the box that says "Check for new messages at startup."

In my T-Bird **Account Settings** isn't under Tools. It is under Edit > Account Settings
I have:

(*) Check for new messages at start up
( ) Check for new message every [10] minutes
(*) Automatically download new messages

T-Bird never starts in my Inbox
**It always starts in *Local Folders*** (even when new messages appear)

At times I see: Getting 2 of 5,  and Inbox is BOLD with (1) beside it, but T-Bird stays at Local Folders.

How can I get it to start in Inbox?
Anyone here know how?

Bruce


Open Thunderbird, choose menu Edit en choose Preferences.
On the tab General it says the following (see attached picture)
**Un**check the item about the Thunderbird start page. The next time you start the program you will see your inbox directly.

Succes,
DeMus

---

