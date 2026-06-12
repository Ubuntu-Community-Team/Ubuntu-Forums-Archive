---
title: "Evolution Notifier"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Webspot on 2006-10-10
Is there a program that allows me to run evolution in the notification tray, and then when there has been a email come in, it alerts me?

This would be great if it's available

Thanks

Andrew Gee

---

### Post by Marsolin on 2006-10-10
It's not specific to [Evolution]("http://linuxappfinder.com/package/evolution"), but there is a program called [Mail Notification]("http://linuxappfinder.com/package/mail-notification") that might work for you.

---

### Post by Webspot on 2006-10-10
Yeah. Okay. I'll give that a go

Thanks!

---

### Post by Big Fish on 2006-10-10
[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

---

### Post by Webspot on 2006-10-11
whilst running "./configure", i got an error saying the it could not find the gnome libraries. what package do i need to install to have them there?

Thanks again

Andrew Gee

---

### Post by Drakkor on 2006-10-11
Thunderbird is a nice e-mail client which you can select a custom audio alert to sound,when mail arrives,plus I like the junk mail options a lot better ! :p

---

### Post by cacharreo on 2006-10-11
Try with **gdesklets**. You can use a lot and funny aplicatons including an email notiffier

---

### Post by Marsolin on 2006-10-11
> **Webspot said:**
> whilst running "./configure", i got an error saying the it could not find the gnome libraries. what package do i need to install to have them there?

Thanks again

Andrew Gee

I suggest installing it through the Ubuntu repositories. The package is called mail-notification.

---

### Post by Webspot on 2006-10-11
> **Marsolin said:**
> I suggest installing it through the Ubuntu repositories. The package is called mail-notification.

Couldn't find it in the repos. I've got all the repos enabled in sources.list

---

### Post by Marsolin on 2006-10-11
It's in the universe repo. Go [here]("http://linuxappfinder.com/package/mail-notification") for direct links to each version from the Ubuntu archive.

---

### Post by Webspot on 2006-10-11
Thanks. It works fine!!!

---

### Post by Hibountu on 2006-10-12
Is there a way to have it work without having evolution started... seems a little pointless to be notified when evolution is open. :-k

---

### Post by tpbarnabas on 2007-07-09
> **Hibountu said:**
> Is there a way to have it work without having evolution started... seems a little pointless to be notified when evolution is open. :-k

fire up a terminal and enter

```
mail-notification -p
```

just add a new pop3 mailbox, enter pop3 server address, userid and pwd.

this way it will check mails without evolution or other client.
good luck!

---

### Post by gregh on 2007-07-19
I wrote a small python script that uses libnotify to alert of a new email (like gaim toaster popups) let me know and I can send it to you.

-Greg

---

