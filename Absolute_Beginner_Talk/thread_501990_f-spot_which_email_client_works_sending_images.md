---
title: "f-spot: which email client works sending images?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by takayuki on 2007-07-16
Hi,

I'm running f-spot 0.3.5 with fiesty xubuntu.

I get an error when I try to email selected images via Thunderbird.

What email client works with f-spot to send images?

thanks,

takayuki

---

### Post by takayuki on 2007-07-16
I figured it out. * (This issue may be specific to xubuntu.  not sure.)*

F-spot uses evolution by default.  If you try to use Thunderbird, the default in Xubuntu, you'll get an error.

Launch gconf-editor via the terminal.  (If it's not installed, then sudo aptitude install gconf-editor.)

In the gconf-editor gui, select Desktop, Gnome, url-handlers, mailto.  Then change the command field to mozilla-thunderbird %s.

This lets f-spot know to use thunderbird to send emails with images.


Then another maddening error kept popping up.  I could only send about half of the emails with images from f-spot.  The answer to this problem was on the f-spot site here: [http://f-spot.org/User_Guide/Share](http://f-spot.org/User_Guide/Share)

The problem was f-spot and thunderbird were only giving me 30 seconds to compose the message and hit the send button.  Any longer and the images were deleted from the tmp directory.

Here's the solution from the f-spot site:

"If you're sending resized pictures, F-Spot will keep the modified versions somewhere in the
/tmp directory for 30 seconds. It's not an issue with evolution, which makes it's own local copy of the
attachments, but could be a bit shorter if you're using thunderbird. You can change the delay by editing
the gconf key /apps/f-spot/export/email/delete_timeout_seconds."

note: again, use gconf-editor to change the timeout_seconds value.  it's a nice, easy gui editor.

I set it to about 2400 sec's.


Hope this helps someone out.

xubuntu, thunderbird, mozilla-thunderbird, f-spot, email images from f-spot, xfce4, f-spot email error

---

### Post by mplon on 2008-05-26
Thanks so much, I just found this through Google and it's exactly what I was looking for. 

Another tip, for the mailto handler, if you pick "exo-open" instead of Thunderbird, this will always use the default that you've set through the Xfce menu (Preferred Applications) -- I use mutt.

---

### Post by rodm1011 on 2008-07-02
Great,  thanks *takayuki*

---

### Post by lisati on 2008-07-02
<aside>I wonder if anyone has successfully run Kodak's "Easyshare" software in Wine. It has an option to email photos without invoking an email client. If I remember, I might research it some time</aside>

---

