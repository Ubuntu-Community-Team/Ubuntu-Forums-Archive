---
title: "How to restore 2 thunderbird accounts in one?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2008-04-02
I have been using thunderbird in windows for one email address and thunderbird in Ubuntu for another email address.

Now I want to move the emails from windows to thunderbird in ubuntu. I have this folder named '4153a3v5.default'. Inside is a lot of crap and also a folder named 'mail' which has another two folder in there: 'Local Folders' and 'mail.mydomain.com'.

Which folder do I now need to add to which folder in ubuntu? I tried several things but nothing got my email to show up in ubuntu next to the emails I already got in there..

Does anybody know?

---

### Post by rrwo on 2008-04-02
The Mozilla website has a page on [merging profiles]("http://kb.mozillazine.org/index.php?title=Thunderbird_:_FAQs_:_Merge_Profiles&redirect=no").

---

### Post by kramer65 on 2008-04-02
I had a good look at it, and I have to create a new profile to merge the two accounts. I appearantly have to do this in the Profile manager (I'm looking at [this page]("http://kb.mozillazine.org/Profile_Manager#Accessing_the_Profile_Manager") for that). 

I 'cd' to /home/myusername/.mozilla-thunderbird and then type
"./thunderbird -profilemanager"
This however gives me an error which says that the file or folder doesn't exist..

What now..?

---

### Post by philinux on 2008-04-02
In the terminal just type

thunderbird -profilemanger

---

### Post by kellemes on 2008-04-02
> **philinux said:**
> In the terminal just type

thunderbird -profilemanger

typo.. ;-)
```
thunderbird -profilemanager
```

---

### Post by kramer65 on 2008-04-02
Thank you! That helps!

Actually the reason why I wanted to do this because i wanted to send many emails to my gmail afterwards. I just found [http://www.gmailuploader.com/](http://www.gmailuploader.com/) which works like a charm!

Thanks anyway, I still need this profilemanager!

---

