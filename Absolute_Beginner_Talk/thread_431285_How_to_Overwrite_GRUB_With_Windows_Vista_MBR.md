---
title: "How to Overwrite GRUB With Windows Vista MBR"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-05-02
If SOMEONE could please tell me how to overwrite BRUB with the Windows Vista 64 bit MBR without having to fresh install Vista it'd be VERY much appreciated.

Thanks in advance.

---

### Post by euler_fan on 2007-05-02
Not being a Windows guru to the extent needed to help, I just want to make a few notes and ask a a question:

Windows being pretty parasitic, unless Vista is about 1 billion times more considerate than XP it will prevent you from booting into Ubuntu if you do what you propose. Are you trying to get rid of Ubuntu from your machine? If so, the best way is a clean re-install of Vista.

Sadly, from everything I have read elsewhere, Vista and Ubuntu are not exactly dual bootable out of the box yet. If you need the Windows functionality it might be worth it to switch back to XP.

---

### Post by smiley2billion on 2007-05-02
I believe you can use the Vista install cd to "repair" installations by booting off the cd.  It has a built in problem finder that should see the MBR needs repairing, if it doesn't detect that I'm also fairly sure it has an option to repair the MBR manually.  If all else fails I know you can use the Vista repair mode to bring up a console, from that you'd need to issue the fixmbr command (I believe it's fixmbr, might have to look up the exact command) and be good to go.


As stated above, this will without a doubt remove your ability to boot into Ubuntu.  To fix that you'd have to reinstall GRUB. However, Vista and Ubuntu are perfectly fine when dual booting.  I'm doing that right now.

---

### Post by confused57 on 2007-05-02
Maybe this will help, I don't use Vista myself:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

---

### Post by euler_fan on 2007-05-02
> **smiley2billion said:**
> . . . Vista and Ubuntu are perfectly fine when dual booting.  I'm doing that right now.

Thanks for the update on that. I may try it someday when I buy my next machine.

---

### Post by dannymichel on 2007-05-02
> **confused57 said:**
> Maybe this will help, I don't use Vista myself:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)
WOW MAN!
IF THERE WERE AWARDS ON THIS SITE OR AWARDS FOR PEOPLE LIKE YOU IN GENERAL I WOULD NOMINATE YOU!
Listen bro, I've been on many many many many forums and NOONE could help with this.
You were the ONLY one that helped.
Thank you so much.
That worked.

---

### Post by starcraft.man on 2007-05-02
> **euler_fan said:**
> Thanks for the update on that. I may try it someday when I buy my next machine.

Shudders... don't support DRM >.> if we all boycott vista, maybe Microsoft will rip out all the DRM and crap and make it a good OS (wishful thinking from an old dos day user). *whistles innocently hopping that bill gates isn't spying on him right now*

---

