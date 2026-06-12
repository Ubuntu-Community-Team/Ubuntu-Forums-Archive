---
title: "Is there a GNOME panel applet like the XFCE mail applet?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by James Bennett on 2007-06-10
I recently switched from XFCE to GNOME for my desktop environment, and really like the mail applet for XFCE. I have Checkgmail, but I'm wanting to get the same functionality for both my school mail account and my website mail account.

My Google fu is insufficient to find a listing of gnome applets anywhere, so...any help?

Thank you for your time,
James Bennett

---

### Post by yabbadabbadont on 2007-06-10
gnubiff may do what you want.  It can be run in its own window or as a gnome panel applet.

---

### Post by llamakc on 2007-06-10
apt-cache show mail-notification

...

Description: mail notification in system tray
 mail-notification works with system trays implementing the
 freedesktop.org System Tray Specification, such as the GNOME Panel
 Notification Area, the xfce4 Notification Area and the KDE System Tray.
 .
  Mail Notification features include:
   * multiple mailbox support
   * mbox, MH, Maildir, Sylpheed, POP3, IMAP, Gmail and Evolution support
   * Mozilla products (Mozilla, SeaMonkey, Thunderbird, ...) mailbox support
   * SASL authentication support
   * APOP authentication support
   * SSL/TLS support (disabled, see README.Debian)
   * automatic detection of mailbox format
   * immediate notification (depends on your settings)
   * HIG 2.0 compliance
 .
  Note: Evolution support is available with mail-notification-evolution.
 .
  Homepage: [http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

---

