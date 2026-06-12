---
title: "E-mail won't display correctly in Evolution"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by susantha on 2006-12-24
Hi All,
  I'm using Evolution mail as my default e-mail program. When I receive some e-mails with HTML pages it won't display properly. I notice this is true in hotmail account also when I access my account through web but they have given a option to click to show the fully content.Wonder if there's a way to fully display the message rather than part of it.
Thanks in advance for any help given in this matter.

---

### Post by PriceChild on 2006-12-24
*moved and bumped*

---

### Post by Spin Doctor on 2006-12-25
It is wise not to have html emails displayed right away without the user confirming first he wants to read the email as HTML...

To do this in Evolution, for the message you want to load all pictures and html:

```
CTRL+I
```I have noticed it there is a slight delay after pressing this key combination,and until the HTML message shows up on your message pane.

---

### Post by Joer4x4 on 2006-12-27
There is a problem displaying html in Evolution. I've had the problem since I installed Ubuntu this past Summer. Graphics overlay text and text overlays text resulting in a partially unreadable email. 

I can't find any info to resolve the problem. When I get a chance I am going to hunt through the config files.

The same emails I have problems with display ok (are readable) in Sylpheed Claws using gkt (as Evolution does). They render perfectly in Thunderbird but Thunderbird is way too slow on my 2Ghz box. It's ashame you can't use Gecko in Evolution!

I submitted a bug report but someone re-assigned it to gtk. I'm not sure gtk is the problem?

BTW... What's so bad about HTML mail? I've used it for years and never had a problem. As long as you know the source...no problem. I never open HTML that I don't recognize!

Plain text doesn't cut in serious conversations and can lead to misunderstandings on complex topics. HTML helps simplify the issues.

Later...

---

### Post by Spin Doctor on 2006-12-28
> **Joer4x4 said:**
> 
BTW... What's so bad about HTML mail? I've used it for years and never had a problem. As long as you know the source...no problem. I never open HTML that I don't recognize!


Basically, I belive this is the HTML email scenario:
Spammers can use <IMG SRC="http://spamserver/**uniqueIDforYOU.gif **/> in your HTML mails, which if run on the client, requests an image from a spam server. Since they use an uniqueID for the image src you are requesting, they can then look at their server to see which emails actually downloaded the "tracing image". After this, count on more spam, since your emailaddress has been verified to exist and that you use it...

Basically, a spammer wants to make sure an emailaddress is valid and being used...Then they sell it to someone else or spam you even more themselves.

This is why most emailclients have options to turn off loading in images. Lately though however, spammers have started to "bake in" images that are actually sent with the message. These they cant trace, however they are tougher to stop in your spamfilters.

If you never open unknown HTML emails you are pretty safe. However, if someone would get hold of one of your friends contact list and you are in it, they could send a "prepared" HTML email from his/her address, and you would think it would be legitimate. 

I prefer textonly emails for highest security. Well, to be absolutely safe, encrypted emails are the way to go, but we will save that for another time. =)

Cheers

---

### Post by Joer4x4 on 2006-12-28
> **Spin Doctor said:**
> Basically, I belive this is the HTML email scenario:
Spammers can use <IMG SRC="http://spamserver/**uniqueIDforYOU.gif **/> in your HTML mails, which if run on the client, requests an image from a spam server. Since they use an uniqueID for the image src you are requesting, they can then look at their server to see which emails actually downloaded the "tracing image". After this, count on more spam, since your emailaddress has been verified to exist and that you use it...

Basically, a spammer wants to make sure an emailaddress is valid and being used...Then they sell it to someone else or spam you even more themselves.

This is why most emailclients have options to turn off loading in images. Lately though however, spammers have started to "bake in" images that are actually sent with the message. These they cant trace, however they are tougher to stop in your spamfilters.

If you never open unknown HTML emails you are pretty safe. However, if someone would get hold of one of your friends contact list and you are in it, they could send a "prepared" HTML email from his/her address, and you would think it would be legitimate. 

I prefer textonly emails for highest security. Well, to be absolutely safe, encrypted emails are the way to go, but we will save that for another time. =)

Cheers

It's not the pictures that bother me - it's the scripts. It's easy to embed junk in scripts. In my opinion, all code should be compiled only for best security. Unfortunately, the way the industry has moved over the past 20 years, scripts are more cost effective to maintain due to all the "junk" the programmer has to code (another story).

As far as text goes, the html or scripts have to be downloaded to sort out the text. Doesn't make much sense to me.

---

