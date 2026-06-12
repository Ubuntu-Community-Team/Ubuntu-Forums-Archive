---
title: "scribus -can't enable color management / cms"
date: 2007-02-18
forum: Art &amp; Design
---

### Post by towsonu2003 on 2007-02-18
I'm too new to scribus. I was trying to follow the online tutorial and I got stuck even before being able to start...

I created a color profile for my monitor using lprof, put it in ~/.color/icc/ , told scribus where to look for this profile at "preferences - general". The problem is, any time I click on Preferences > Color Management, scribus tells me that "Color management is supported but cannot be currently enabled. Make sure you have ICC color profiles installed and that the profile path in the preferences points to where they're installed"...

as I mentioned, I created a new color profile and put it to ~/.color/icc and set the scribus preference accordingly.

Can anyone help? I'm using Dapper.

---

### Post by deanjm1963 on 2007-02-18
You need to install more icc profiles than just your monitor. add the scribus.net dapper repos to your repository list. check out [http://www.scribus.net]("http://www.scribus.net") and click on "debian repository with instructions", there are repos for dapper, etc.

hope this helps

---

### Post by towsonu2003 on 2007-02-18
> **deanjm1963 said:**
> You need to install more icc profiles than just your monitor. add the scribus.net dapper repos to your repository list. check out [http://www.scribus.net]("http://www.scribus.net") and click on "debian repository with instructions", there are repos for dapper, etc.

hope this helps

thanks, I'll try adding the icc profiles from the site. the repo seems to only have a new version of scribus though?

---

### Post by towsonu2003 on 2007-02-18
yes, the icc profiles from their site solved the issue. Thanks a lot :)

---

