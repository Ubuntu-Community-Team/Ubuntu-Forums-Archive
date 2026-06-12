---
title: "refit - want to change windows icon to penguin on boot up"
date: 2010-01-24
forum: Apple Hardware Users
---

### Post by hollowtd on 2010-01-24
I got ReFit installed on my macbook but I get two icons: the apple and a grey windows sign. I want the penguin, so any ideas on how to change the horrendous Windows icon to the cute much-wanted penguin?

---

### Post by linuxopjemac on 2010-01-25
Go to OSX, the EFI partition. You will find the icons in there. Rename or copy the linux icon into legacy OS, as that is what rEFIt thinks it is.

---

### Post by hollowtd on 2010-01-25
I can find a folder called efi and I can find a folder full of icons. I just don't know how to get those into Legacy OS. CAn you walk me through getting to the right folders?
Cheers

---

### Post by hollowtd on 2010-01-26
Not sure how to move them, as they seemingly have the same file name extensions (the icons).

---

### Post by linuxopjemac on 2010-01-26
Here is my icons folder...

---

### Post by hollowtd on 2010-01-26
Thanks for that. I simply took the os_legacy.icns name away from the windows icon and moved it to the penguin and that did the trick. Thanks for sending me a picture as that helped a lot. I've been tired of staring at the windows logo for a month now. Cheers!

Essentially- rename the icon picture in the efi folder os_legacy.icns if you want that to be the picture that shoes up under rEFIT. Another penguin icon is also named boot_linux.icns. Restart and should work.

---

