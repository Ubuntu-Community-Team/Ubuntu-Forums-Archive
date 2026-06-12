---
title: "Lubuntu 14.04.1 LTS on Imac G5 Powe PC instalation issues."
date: 2014-11-20
forum: Apple Hardware Users
---

### Post by slawek2 on 2014-11-20
Hello
I have Imac G5 Power PC with nvidia geforce.
I run Lubuntu 14 live cd on it and everything was great - no problems so i decided to install this distrybution on my imac. After installation, there is a problem with display screen. After screen with Lubuntu logo, white screen appear with black horizontal lines and nothing more. But i can still run live version from dvd and its working with no problem. How can i fix this problem

Thanks

---

### Post by este.el.paz on 2014-11-21
More than likely you need to either get or set up the xorg.conf file appropriate for your computer . . . you can search here or on the PowerPCFAQ to find out how to do that exactly . . . .

e.e.p.

---

### Post by rican-linux on 2014-11-21
Also try on the yaboot prompt this

"Linux video=radeonfb:_1280x854-32@60_"

Substitute the underlined portion with your display settings.

---

### Post by este.el.paz on 2014-11-21
> **slawek2 said:**
> Hello
I have Imac G5 Power PC with nvidia geforce.
Thanks
> **rican-linux said:**
> Also try on the yaboot prompt this

"Linux video=radeonfb:_1280x854-32@60_"

Substitute the underlined portion with your display settings.

@r-l:

Notice that he said "with nvidia geforce" . . . which would possibly indicate some other boot parameters.

e.e.p.

---

### Post by rican-linux on 2014-11-21
you are right. apologies

---

### Post by este.el.paz on 2014-11-21
@r-l:

Cool.  You were trying to help . . . but sometimes a good thing isn't always a good thing, all of the time . . . .  : - )  Should be the boot params will be listed in the FAQ . . . but these days the 14.04 for PPC seems to need the xorg.conf file to be set up . . . .  Which requires some reading to be done by the OP.

e.e.p.

---

### Post by rican-linux on 2014-11-21
I hear ya, that was a huge lesson I learned when I went through an Arch install. All the info is there if you only read the wiki.

---

