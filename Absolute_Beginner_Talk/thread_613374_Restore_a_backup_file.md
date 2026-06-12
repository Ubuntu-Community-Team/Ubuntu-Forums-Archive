---
title: "Restore a backup file"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by mubelhor on 2007-11-14
I want to start experimenting with the config file.  I think I understand that executing:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

in terminal mode will backup my current file.  If I get things messed up, do I just reboot in recovery mode and execute:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf   ??

Or do I need to "cp" that backup file to a different directory, rename it "xorg.conf", and then use the "cp" command to overwrite the messed up file?   It's the "backup" file extension that's making me hesitate.

---

### Post by st33med on 2007-11-14
Yes, exactly as you said. It should overwrite the data.

---

### Post by Dr Small on 2007-11-14
> **st33med said:**
> Yes, exactly as you said. It should overwrite the data.
+1
As st33med said.
You have it right.

---

### Post by nhandler on 2007-11-14
> **mubelhor said:**
> I want to start experimenting with the config file.  I think I understand that executing:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

in terminal mode will backup my current file.  If I get things messed up, do I just reboot in recovery mode and execute:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf   ??

Or do I need to "cp" that backup file to a different directory, rename it "xorg.conf", and then use the "cp" command to overwrite the messed up file?   It's the "backup" file extension that's making me hesitate.

That command should work correctly. However, it will leave you with a xorg.conf and xorg.conf.backup. In order to eliminate the xorg.conf.backup, use this command instead:

```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by mubelhor on 2007-11-14
> **st33med said:**
> Yes, exactly as you said. It should overwrite the data.

Which action am I safe with?  Am I safe with:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf     ?

My messed up config file will  be replaced by the backup file, and I will have a duplicate file in the same directory but with a "backup" extension?  (I don't know how to respond to multiple replies in one message.)  Other than the extra file, I don't need to worry about the "backup extension?

---

### Post by Inxsible on 2007-11-14
> **mubelhor said:**
> Which action am I safe with?  Am I safe with:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf     ?

My messed up config file will  be replaced by the backup file, and I will have a duplicate file in the same directory but with a "backup" extension?  (I don't know how to respond to multiple replies in one message.)  Other than the extra file, I don't need to worry about the "backup extension?yeah just let it stay there...you can at a later time go back delete them if you like, but please be careful while doing this.

---

### Post by mubelhor on 2007-11-14
> **Inxsible said:**
> yeah just let it stay there...you can at a later time go back delete them if you like, but please be careful while doing this.

Great!  Thank you all!  I think that the best way for me to feel comfortable with abandoning MS Windows is to feel free to screw things up and know that I can recover.

---

### Post by Dr Small on 2007-11-14
> **mubelhor said:**
> Great!  Thank you all!  I think that the best way for me to feel comfortable with abandoning MS Windows is to feel free to screw things up and know that I can recover.
Yes. lol, I love that feature :p

---

### Post by Inxsible on 2007-11-14
> **mubelhor said:**
> Great!  Thank you all!  I think that the best way for me to feel comfortable with abandoning MS Windows is to feel free to screw things up and know that I can recover.
Glad to help. Thats the best thing about Linux, you can always recover ;)

everything is free...so its not like you have to pay for X number of tries ;)

also the best thing about Ubuntu is this forum, where there is a lot of support.

---

### Post by mubelhor on 2007-11-14
> **Inxsible said:**
> Glad to help. Thats the best thing about Linux, you can always recover ;)

everything is free...so its not like you have to pay for X number of tries ;)

also the best thing about Ubuntu is this forum, where there is a lot of support.

I agree!  My Firefox bookmark folder is filling up with links to the "howto's" and tutorials from this forum.

---

### Post by Dr Small on 2007-11-14
> **mubelhor said:**
> I agree!  My Firefox bookmark folder is filling up with links to the "howto's" and tutorials from this forum.
Mine too :p

---

### Post by Inxsible on 2007-11-14
> **mubelhor said:**
> I agree!  My Firefox bookmark folder is filling up with links to the "howto's" and tutorials from this forum.

> **Dr Small said:**
> Mine too :pyou guys should start using del.icio.us or digg or stumble upon ;)

---

### Post by Dr Small on 2007-11-14
> **Inxsible said:**
> you guys should start using del.icio.us or digg or stumble upon ;)
Oww. Nice :)
*Dr Small is now trying out del.icio.us

---

### Post by ntu on 2007-11-15
After executing each of the commands, you could go into Places>Computer>File system>/etc>/X11 to see what has happened.

---

### Post by mubelhor on 2007-11-16
It looks to me as if I have way too many backup files.  My system seems to be stable.  Should I remove some (most of) these)?

---

### Post by Inxsible on 2007-11-16
yes you can remove them except the one which is named xorg.conf :)

I would recommend that after deleting all of them you make a backup of the current one again...just to be safe :)

---

