---
title: "Does such a tool exist?"
date: 2007-10-11
forum: Art &amp; Design
---

### Post by bean77 on 2007-10-11
I have my photos spread out over 5 or 6 photo hosting websites.  Short of spending the hours to "save as: from the original site and uploading to the new site, there has to be a better way, right?

---

### Post by Chymera on 2007-10-11
as far as I know, if the sites don't have ftp access you'll just have to go ahead and start being sorry for not thinking about this scenario when saving your files... :-P

---

### Post by argie on 2007-10-11
If the site has a thumbnail list, you might be able to get away with using a Firefox extension like DownThemAll. No guarantees though.

Also, if you can access the files as direct links and they're numbered in a standard way like:
[http://site.com/images/bean77/11102007.jpg](http://site.com/images/bean77/11102007.jpg), [http://site.com/images/bean77/10102007.jpg](http://site.com/images/bean77/10102007.jpg), [http://site.com/images/bean77/09102007.jpg](http://site.com/images/bean77/09102007.jpg) you might be able to write a for loop in bash and use wget to get the files. Alternatively, if visiting [http://site.com/images/bean77/](http://site.com/images/bean77/) will give you a directory listing, using wget in recursive mode should get you what you want. I don't know of any other way, sorry.

---

### Post by Ralphie on 2007-10-11
depending on how the sites are structured, you might be able to use firefox extensions like:

Download them all:
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)
flashgot:
[https://addons.mozilla.org/en-US/firefox/addon/220](https://addons.mozilla.org/en-US/firefox/addon/220)

and there is another one that saves pictures from tabs, so youd be able to open a bunch of tabs with your large version picture in it and it will automatically go through, save the picture and close the tab, but i cant remember the name. if someone does, please post!

---

### Post by Ralphie on 2007-10-11
forget that dude on the first reply.. what kind of answer is that?

heres the tab one, this is your last resort,
[https://addons.mozilla.org/en-US/firefox/addon/3404](https://addons.mozilla.org/en-US/firefox/addon/3404)

middle click (the scrolly wheel on the mouse, press it down) on the links to the large version images so that they open alone in tabs, then use the extension to automatically go through and save each pic from each tab

---

### Post by Officer Dibble on 2007-10-11
It's a bit tricky without knowing what sort of sites they are, access they allow, and also security.

Maybe you could start by just saving the page via Firefox? All the images are typically saved into a separate folder.

In the old days there were apps that could just suck the entire contents of a website right off the server... but those days are long gone I think.

Hope it works for you or that someone one else comes along with a friendly suggestion.

---

### Post by bean77 on 2007-10-12
I will have to try these during my kids' naptime tomorrow...thanks!

---

### Post by !nkubus on 2007-10-12
I didn't try it myself but conduit is what you looking for:

[http://www.conduit-project.org/](http://www.conduit-project.org/)

EDIT:
oops sorry I missread your post you want to do the inverse.

---

### Post by bean77 on 2007-10-17
I'm not able to get Downloadthemall to work...I mean, I installed, it, etc.  But I am unsure of the exact address to use.

The thumbnails are 96x96...

I'm using Shutterfly

---

### Post by bean77 on 2007-10-17
Got it to work but the pics are saved as thumbnails.  I want them regular sized so I can upload them to Snapfish...

---

### Post by !nkubus on 2007-10-17
[https://addons.mozilla.org/en-US/firefox/addon/3177](https://addons.mozilla.org/en-US/firefox/addon/3177)

maybe auto slide show for FF , there is a button Save all :)

---

### Post by bean77 on 2007-10-17
I like DownLoadThemAll the best out of the several suggested here.  But I can't get past the thumbnail thing.  What am I doing wrong?

---

### Post by bean77 on 2007-10-17
Anyone?

---

### Post by Lord_Dicranius on 2007-10-19
DownThemAll will only bring up the links for the media that's on that page.  I'll play around with a few things this weekend, see what I can come up with.

---

### Post by Lord_Dicranius on 2007-10-20
Ok, well I don't have a Shutterfly account, so I just Googled "shutterfly album" to see what I could come up with.  How is the page formatted?  Does it look something like [this](http://shutterfly.blog-city.com/photo_album_6.htm)?  With the thumbnails opening the pictures directly (linking directly to .jpg)?

---

### Post by bean77 on 2007-10-20
Yes, it's that type of thing.  The pictures on the page of thumbnails do dot have file extensions on  them.  For instance:  47b7ce35b3127ccebd8e9182c0a700000050100AcsnLZo4atGOA

In DtA, they are not picked up as jpegs.  They have no filetype associated with them at all.

---

### Post by Lord_Dicranius on 2007-10-20
Yeah, I don't know.  I had my wife sign into her Shutterfly account so I could get a better idea, but it looks like all the links are encoded as you pointed out above.  Using DownThemAll, the links to the full size images don't show up on the "Links" tab, and they won't show up on the "Pictures and Embedded" tab either as that only brings up what's on the current page there.  Aside from going to every single picture, right-clicking and selecting save image, it looks like the only other option I can see is this [archive CD](http://www.shutterfly.com/shop/product_c10046-p2017/Image_Services_Archive_CDs) they offer.  I found that when [searching their customer service page for "download"](http://crmweb.shutterfly.com/cgi-bin/helpfly.cfg/php/enduser/std_adp.php?p_faqid=181&p_created=1127403058&p_sid=u66-oGOi&p_accessibility=0&p_redirect=0&p_lva=&p_sp=cF9zcmNoPSZwX3NvcnRfYnk9JnBfZ3JpZHNvcnQ9JnBfcm93X2NudD0zOSZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1kb3dubG9hZA**&p_li=JnBfdXNlcmlkPTAwMDA3NTc1ODkwNSZwX2VtYWlsPXRlcnJ5cmFlNUBnbWFpbC5jb20mcF9wYXNzd2Q9MTIzNCZwX2ZpcnN0X25hbWU9VGVycnkmcF9sYXN0X25hbWU9T3J0aXomcF9jY2ZfMjI9U0ZMWSZwX2NjZl8yMD1TRkxZJnBfY2NmXzIxPVdFQiZwX2NjZl8yND10ZXJyeXJhZTVAZ21haWwuY29tJnBfY2NmXzI1PWZhbHNl&p_topview=1).

Sorry I couldn't have been more help :-(

---

### Post by bean77 on 2007-10-22
Thanks, I appreciate you checking back in!

---

### Post by Lord_Dicranius on 2007-10-22
> **bean77 said:**
> Thanks, I appreciate you checking back in!
Just trying to help :)

---

