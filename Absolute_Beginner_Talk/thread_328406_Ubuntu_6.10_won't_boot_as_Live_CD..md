---
title: "Ubuntu 6.10 won't boot as Live CD."
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by RussianVodka on 2006-12-30
I don't know why. It used to work just fine. Then I went and installed Windows, and when I went to go install Ubuntu again (on my other partition), it won't boot up. It goes through the whole process of showing me the logo and the loading bar, but then it just goes to a black screen with a blinking underscore. No error message or nothing. And it just stays like that?

Why is this? Did Microsoft do something to my HD when I installed Windows?

---

### Post by raul_ on 2006-12-30
as long as it keeps blinking just wait...if it stops blinking then you have a problem. Check if your cd is spinning

---

### Post by wagoatzuki on 2007-01-03
This seems to be a very very common ordeal and it is related to the display. This has happened to me on 3 different occasions, as a matter of fact Ubuntu has only booted the livecd on 2 machines for me to date out of 6. The other machines go to black screen right after the progress bar. One of those 2 machines that actually did work had a black screen but I fixed it by using a vga cable instead of a dvi cable. Once I plugged in the vga cable Ubuntu was waiting for me to finish the install. I assume this is the case with all or most of the screens that go black during livecd booting because I see Hard drive activity and cdrom activity for about 30-50 seconds after all goes dark on the screen. It appears everyone knows about it but if your one of the unlucky few to bad for you. You'll get suggestions to try dapper or modify your xorg.conf but dapper will likely do the same thing and how do you configure your xorg if you cant even get a console?? Think it's just one of those things, go buy different hardware....](*,)

---

### Post by raul_ on 2007-01-03
Sometimes adding a boot option like noapic or nolapic works

---

### Post by RussianVodka on 2007-01-04
Never mind. It was a busted CD. Or at least I think it was. I burned another CD, and it worked fine. Which is odd, considering that the busted CD worked perfectly just a week prior to this.

---

