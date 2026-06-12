---
title: "Installing some sort of ATi for edgy."
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by deethree on 2006-12-09
Trying to get my ati driver installed and working correctly. 

I've followed:
(method #2)
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) 

and then: 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d01742cec183112be090e459b74129606e258f79](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d01742cec183112be090e459b74129606e258f79)

and I'm still using they mesa driver.

If anyone wants to hackinto my computer and get this working... ;) 

but seriously, I'm kind of at a stand still.  I've got to eat something, then I might go back and try method #1 from the first link.

If anyone has any input I'd like to hear it. ](*,) 

Thanks for your time.

d3.

---

### Post by lhtown on 2006-12-10
There is tons of stuff in the forums and ubuntuguide.org and other places about this.

Without knowing what error messages you are getting or specific problems you are having and the card you have, you probably won't get any help.

If you are still having problems after searching some, provide as many details as possible and maybe someone will take the time to try to help.

---

### Post by igknighted on 2006-12-10
Wow, I read that guide and I never had to do all that.  I just did:
```
sudo aptitude update
```
```
sudo aptitude install xorg-driver-fglrx
```
```
sudo aticonfig --initial
```
And thats it, worked fine.

That said, what ATI card do you have?  It makes a big difference what will work and what wont.  The new ATI cards (x1000 and up) struggle mightily in linux (especially the open source radeon driver)

---

