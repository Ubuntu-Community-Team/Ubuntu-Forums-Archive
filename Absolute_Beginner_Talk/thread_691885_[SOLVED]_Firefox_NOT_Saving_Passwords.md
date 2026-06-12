---
title: "[SOLVED] Firefox NOT Saving Passwords"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2008-02-09
So I'm having issues, I have it set in firefox to save my passwords when I go to certain sites but on every thing I log in it asks to save it and I will select yes and it doesn't save it, I just get the "do you wanna save" box again next time. Can anyone help me fix this so I can be saving passwords and saving time yet again? Thanks!

---

### Post by randy78 on 2008-02-09
What version of Firefox are you using (Help>About, it will tell you the version number)

I personally use Keepassx to manage all of my passwords...

sudo apt-get install keepassx

KeepassX is a bit like Roboform

---

### Post by Tumpster on 2008-02-09
Version 2.0.0.12

---

### Post by randy78 on 2008-02-09
I cannot locate much info on it through Google...

If you can't get it resolved, I think you should give KeepassX a shot.

You'll probably never use another password management program again!

Take Care

---

### Post by earobinson on 2008-02-09
do you have any weird extentions like google browser sync installed?

also how manny passwords have you saved so far?

---

### Post by Tumpster on 2008-02-09
No passwords saved and I only have forecast fox on here.

---

### Post by earobinson on 2008-02-09
weird, you could always blow away (deleat) your .mozilla dir and start from scratch see if that fixes it.

also do you have any space left on your hd?

---

### Post by Tumpster on 2008-02-09
I have plenty of space left on my hard drive (round 50gbs) and might blow the whole thing later. Ideas?

---

### Post by Moop on 2008-02-09
You could try creating a new profile and see if it saves passwords. That would tell you if your profile is messed up. In terminal type ```
firefox -ProfileManager
```

Also, Firefox3.0beta is available in the repos. You can have both versions installed.

---

### Post by y-lee on 2008-02-09
try removing your **signons.txt** file from **/home/username/.mozilla/firefox/default***

and see if this helps

oddly enough mine is called  **signons2.txt **. I have alot of extensions maybe one of them did that.:lolflag:

---

### Post by Tumpster on 2008-02-09
I'm at work right now but I'll definatly give either of those a try! Thanks!! :)

---

### Post by Tumpster on 2008-02-13
Ok, so I tried the deleting signons to no avail, I tried profile manager to no avail. How can I delete or whipe my firefox directly cleanly without harming anything else and how can I load up with no troubles? Thanks!

---

### Post by y-lee on 2008-02-13
One thing you can check is type **[noparse]about:config[/noparse]** into the address bar and then type **signon.prefillForms** into the search on [noparse]about:config[/noparse], is the value set to true? If not double click it to change it to true.

> How can I delete or whipe my firefox directly cleanly without harming anything else and how can I load up with no troubles?

Do you mean by wipe uninstall firefox, how was it installed? If it is the default firefox that comes with gnome then I think you may not be able to uninstall it. But you can try reinstall it thru synaptic package manager. Open up synaptic and find firefox and right click and check reinstall. and then hit apply in synaptic.

If firefox was installed some other way then let me know. The reason I'm asking is because i have 3 versions of firefox on my machine, One came with dapper and two i installed.

You can also try downloading [swiftweasel ]("http://swiftweasel.tuxfamily.org/")and install it. Swiftweasel is just an optimized for speed version of firefox.

**EDIT:** also check **signon.rememberSignons** and tell me what you get for **signon.SignonFileName** also (in about config)

---

### Post by y-lee on 2008-02-13
> **Tumpster said:**
> So I'm having issues, I have it set in firefox to save my passwords when I go to certain sites but on every thing I log in it asks to save it and I will select yes and it doesn't save it, I just get the "do you wanna save" box again next time. 

 One more thing under preferences in FF and security if you click show passwords are the websites for the  passwords you have saved showing up. If you click show passwords are the passwords there?

and when you deleted signons.txt did you also have signons2.txt. If so try deleting both.

EDIT: Also if the saved passwords are showing up in preferences then next time you go to a logon page for a site where the passwords have previously been saved and the username and password is not auto filled  try reloading  the page by hitting F5 and see if that works.

---

### Post by Tumpster on 2008-02-13
Nothing for all those options, I unloaded and reloaded it and nothing helps. The passwords are NOT being saved, I can input one to be saved and it says it's saved but I look under preferences and theres nothing there........

---

### Post by y-lee on 2008-02-13
> **Tumpster said:**
> Nothing for all those options, I unloaded and reloaded it and nothing helps. The passwords are NOT being saved, I can input one to be saved and it says it's saved but I look under preferences and theres nothing there........

Ok Nothing for all those options is odd. I think at least the sigons stuff *should* be standard install for firefox. I'm not sure i mess with my about config file *alot.*

What are the permissions for your /home/username/.mozilla folder, the firefox folder under it and the profile(s) folders under it? Also what is the permissions for the signons.txt, signons2.txt and key3.db files found in your firefox profile folders. (key3,db may be called key2 or something look for key*.db where * is a number)  I once changed the owner of that stuff to root ...doing something stupid don't ask :lolflag: Anyway are you the owner and can you read and write there?

---

### Post by Tumpster on 2008-02-14
FIXED!
I whiped out mozilla/firefox through synaptic package manager, rebooted, made sure the mozilla file was no longer there, reinstalled and rebooted again. Works perfectly now! Thanks for all the help!

---

### Post by y-lee on 2008-02-14
Probably the best idea your about config seemed like it was messed up to me. Reinstall usually works. Glad to hear it went ok.

---

