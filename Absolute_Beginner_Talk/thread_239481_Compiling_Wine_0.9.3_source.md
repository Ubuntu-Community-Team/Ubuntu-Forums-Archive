---
title: "Compiling Wine 0.9.3 source?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Clockwork Clock on 2006-08-19
When I use ./configure in the wine home directory, it gives me these messages:
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
 Can anyone help? I'm new to linux.

---

### Post by Marsolin on 2006-08-19
Is there a reason you are trying to compile it instead of installing it using Synaptic?

---

### Post by Clockwork Clock on 2006-08-19
I never checked for the binary..But I need the 0.9.3 version not *.4. I didn't think Synaptic gave you a choice.

---

### Post by jimmygoon on 2006-08-19
"sudo apt-get install build-essentials"

And I though Synaptics would let you choose older versions... no?

---

### Post by bodhi.zazen on 2006-08-19
Try the available version in synaptic first.

If that will not work, download an older deb package.

Try here:

[http://sourceforge.net/project/showfiles.php?group_id=6241](http://sourceforge.net/project/showfiles.php?group_id=6241)

You should not have to compile wine.

---

