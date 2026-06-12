---
title: "Keyboard Mods... Control _R?"
date: 2011-01-29
forum: Apple Hardware Users
---

### Post by SwarfEye on 2011-01-29
Hi,

I'm running 10.10 on my macbookpro7.1, and generally thing are going quite well.  I've been really delighted with the guidance given on this page...

[https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)

Specifically, I've used the keyboard modification suggestions, and they are working quite well.  Now, I want to modify my xmodmap file so that I can uses the right command button as well as the left one... but I having a lot of trouble figuring out what exactly is going on and how this xmodmap stuff works.

Could someone please suggest a way to add right command functionality to this file? 

```

!
! xmodmap script to swap right control & right command key
!

! remove both keycodes (to which Control_L & Super_L is attached)
!     from previous modifier map
remove control   = Control_L
remove mod4      = Super_L Hyper_L

! swap keysyms
keysym Control_L = Super_L Hyper_L
keysym Super_L   = Control_L

! re-add both keycodes to respective modifier maps
add    control   = Control_L
add    mod4      = Super_L Hyper_L

! ***** end of source *****

```

Thanks,

B

---

### Post by SwarfEye on 2011-02-01
I know I'm not the only one out there who is looking for this!

Anyone else out there looking for this too?

B

---

