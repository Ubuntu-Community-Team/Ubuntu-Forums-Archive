---
title: "POP email help needed"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Zzzach on 2008-02-07
I want to use pop email. Is there a way to have it automatically start up and check for new email when I log in to ubuntu? I configured evolution but it didn't notify me that I had any new email until later when I started evolution my self and manually clicked to check/send mail. It seems like this should be done automatically at start up. Should I just use Thunderbird or another pop program? Thanks

---

### Post by pieisgood4589 on 2008-02-07
Just add it to one of the startup apps under "sessions"

---

### Post by Zzzach on 2008-02-07
Then it will automatically check for new email?

---

### Post by andrewjoy on 2008-02-07
Not quite

Go to 

Edit > Preferences >Edit > Receiving Options

And check the check for new emails automaticly

Then 

Edit > Preferences > Mail Preferences > Beep On New Mail

And there ya  Go all done

---

### Post by Zzzach on 2008-02-07
Oh ok thanks... one last question: Does evolution have to be running to check email? Do I have to leave it running all the time or will it run in the background?

---

### Post by andrewjoy on 2008-02-07
I think it has to be open but i am not 100% sure.

I would like to know this too.

A tray icon like pidgon and amarok would be nice but i dont know about this for evolution

---

### Post by Zzzach on 2008-02-07
Ok well I'll test it out and see. Thanks for the help.

---

### Post by jw5801 on 2008-02-07
Yeah, AFIK Evolution doesn't have a tray icon, there might be a plugin for it somewhere. You could also give "alltray" a shot, it's in the repositories and you can use it to run any application with an icon in the tray so you don't constantly need the window open. Personally I use Thunderbird with the tray icon plugin installed.

---

### Post by astoltz on 2008-02-07
I use mail-notification.  It's a gnome panel applet that checks multiple mail boxes - it'll even do gmail.

---

### Post by Zzzach on 2008-02-07
Alright cool, I got mail-notification set up now :guitar:

---

### Post by andrewjoy on 2008-02-08
Thanks astoltz been looking for this for a while now was |.| < this close to resurrecting my realy poor c++ skills to make one myself :P

---

### Post by HippyRandall on 2008-02-08
I have tried repeatedly to get mail notification running nicely with gmail but it always returns errors for me. Can anyone give the specific settings to make it work properly?

TIA

---

### Post by astoltz on 2008-02-09
> **HippyRandall said:**
> I have tried repeatedly to get mail notification running nicely with gmail but it always returns errors for me. Can anyone give the specific settings to make it work properly?

When you set up a new mailbox, one of the "types" is gmail.  The rest is pretty straight forward.  What error are you getting?

---

### Post by HippyRandall on 2008-02-09
mostly generic read errors. the only way I can get it to work is to chose "Evolution" instead of pop or gmail but even then it doesn't tell me when I have new mail. I use Alltray to put evolution into the tray and I don't get any notifications on new mail from it or the mail notification app. /shrug

EDIT:
ok got it working by having it watch evolution inbox but I have different folders for each account so I had to make it watch my gmail folder. Wish there was a way to have it recurse sub directories.

---

### Post by LeDechaine on 2008-02-12
*Mail-notification* didn't even worked for me.

It wasn't even able to check for pop e-mails, and yes, I verified and re-verified: I had written the right hostnames/usernames/passwords.
The "check at every (X) mins" option couldn't even be modified and was "locked" at 5mins.

Anyway, this program was lacking some functionalities I wanted too, so i'm now searching for another mail notification client.

---

