---
title: "Ubuntu Firefox Gmail Password Issue"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Andavane on 2007-08-01
Dear Members
One thing which impressed me with Ubuntu/Firefox was its offer to remember my passwords for me; so when I accepted with "yes", I just had to click in my "user name" and the password was remembered.

Then, because some user names were typed in wrong, I went "Tools/clear private data" in FireFox, in order to make a fresh start.

Now after I had done this, I had to re-enter my passwords for various things and I noticed that: For nearly all my accounts, Firefox offered to remember my password in future occasions.

However for Gmail (which Firefox offered the first time I used it in Ubuntu) it didn't offer to remember the password, and it didn't remember the password either. So for my Gmail account I now have to type the password in every time (as I always have to do in Windows).

Does the team have any ideas why the password should be remembered on the first occasion but not on subsequent occasions? I've tried clearing out my private data (and cookies) on several occasions, but so far, no luck!

Is there something else I could try?

Kind regards

John

---

### Post by guilly on 2007-08-01
Not sure as to why firefox would not remember your gmail password. But have you ever tried using Evolution or some other type of email client to view your email from your gmail account? I find it much quicker and more convenient to use a client of that type.

---

### Post by Andavane on 2007-08-01
> **guilly said:**
> Not sure as to why firefox would not remember your gmail password. But have you ever tried using Evolution or some other type of email client to view your email from your gmail account? I find it much quicker and more convenient to use a client of that type.
No I haven't thought of doing that, but I'll certainly give it a try.
Does it just "go and get it" or something?
Regards
John

---

### Post by asmoore82 on 2007-08-01
In **Firefox**

goto "Edit -> Perferences"
and click on the "Security" Tab
under the "Passwords" Section,
click the "Exceptions" button

HTTPSgoogle should be a global exception.

You can remove it if you want but for some reason it is a pre-defined
exception everywhere; I haven't ever had the password stuff in Firefox
enabled but HTTPSgoolgle is still in my exceptions list.

---

### Post by Nekiruhs on 2007-08-01
> **Andavane said:**
> No I haven't thought of doing that, but I'll certainly give it a try.
Does it just "go and get it" or something?
Regards
John
Yeah. I use Mozilla (The people who make Firefox) Thunderbird 2 for my Gmail account. It is much easier to setup than in Thunderbird 1.5. On first run, it asks what kind of account you have (Yahoo, Msn, Gmail, etc), you select Gmail, and enter in your email address. Then it tries to get your mail, it asks for your password, enter it, select the remember password box. Presto, your done.

---

### Post by guilly on 2007-08-01
> **Andavane said:**
> No I haven't thought of doing that, but I'll certainly give it a try.
Does it just "go and get it" or something?
Regards
John

yes basically. All you need to do is go into settings once your inside your gmail account. You'll see an option to enable pop basically just enable pop then go into evolution create an account your username with be your complete email address therefore [email]name@gmail.com[/email]  pop: pop.gmail.com smpt: smtp.gmail.com. You will also need to set the different incoming and outgoing ports I believe incoming will be 25 and outgoing is 465 (don't quote me on that)

If you look inside your gmail settings i believe there is a link to a how to configure Microsoft outlook for gmail, just use those same settings, Obviously your environment will be different btu the settings are still all the same!

hope this helps.

btw once this is configured there will be no need to type in your username and password everytime just open up evolution and your emails will automatically be downloaded from the web. And also there is a setting that you can select to keep a copy of your emails onto your gmail account that way if your ever not at home you can still log into gmail and check for new emails

---

### Post by Andavane on 2007-08-02
> **asmoore82 said:**
> In **Firefox**

goto "Edit -> Perferences"
and click on the "Security" Tab
under the "Passwords" Section,
click the "Exceptions" button

HTTPSgoogle should be a global exception.

You can remove it if you want but for some reason it is a pre-defined
exception everywhere; I haven't ever had the password stuff in Firefox
enabled but HTTPSgoolgle is still in my exceptions list.

This has done the trick.
Many thanks!   :cool:
Regards
John

---

