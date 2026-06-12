---
title: "Bin install problem"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by deuchar1 on 2007-05-01
Hey guys,

I've downloaded something here and it's a .bin file. I've tried double-clicking it and running it from terminal to get it to install but I keep getting the error:

Cannot open <file>
PlaneShift_CBV.3.018.bin: No application suitable for automatic installation is available for handling this kind of file

Does this mean I'll need to download an additional package to handle installation? Anyone have any ideas?

Thanks,
Graham

---

### Post by deuchar1 on 2007-05-01
Sorry, problem solved. I set chmod +x permission on the file and ran it with a dot slash prefix and it seemed to work....

sudo chmod +x file.bin
./file.bin

:)

---

### Post by justleen on 2007-05-01
if its an executable, you should be able to run it.
If its a CD image, you will have to mount it...

---

