---
title: "Hooking up to the interwebs..."
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Justin125 on 2007-06-23
I need some step by step instructions for getting my D-Link DWL-G122  Revision A2 to work.

I've heard that I need something called ndiswrapper, could someone explain in simple terms what I need to do?

---

### Post by viciouslime on 2007-06-23
Here you go: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Ndiswrapper lets you use a windows driver for your wireless card.

---

### Post by Justin125 on 2007-06-23
"<!> These instructions apply only when using the x86 Alternate CD. If you are running Ubuntu for AMD64, please see NdiswrapperOnAMD64 for instructions. These instructions do not apply to Ubuntu for Power PC (PPC) and the Ubuntu Desktop CDs."

Umm...

Still go ahead?

???

---

### Post by Justin125 on 2007-06-23
Bump...

Should I just follow anyway?

---

### Post by Justin125 on 2007-06-23
OKAY:

I started to follow the steps and downloaded those .deb files and then typed in:

sudo dpkg -i ndiswrapper-common_*.deb

and recviced the following:

dpkg: requested operation requires superuser privilege

---

I'm going to assume the only fix is to get those... How? Or why don't I have them?

(sorry for triple reply but this post is needed)

---

