---
title: "double kernel listing"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-12-01
Hi everyone, I haven't posted much lately because everything is running hunky dory. Just a quick question.
My boot screen shows this;
ubuntu, kernel 2.6.15-27-386
ubuntu, kernel 2.6.15-27-386 (recovery mode)
ubuntu, kernel 2.6.15-26-386
ubuntu, kernel 2.6.15-26-386 (recovery mode)

then the usual stuff re memtest etc.

Just after my first install I got trigger happy and pressed the cursor button during boot-up prior to the boot screen showing and it all went a bit funny then showed the above. I've since reinstalled Dapper (because of a different stuff up) and this still shows the same. It hasn't caused any problems that I'm aware of, but that doesn't mean much.
I'm happy to leave it as it is but I'm wondering if it could cause me difficulties down the track?

Dopey.

---

### Post by CatKiller on 2006-12-01
Whenever you install a new kernel, it keeps the old one in case the new one doesn't work. Once you've tested that the new kernel works, you can safely remove the old one with Synaptic. This will also remove it from this list for you.

---

### Post by carloslosgrande on 2006-12-04
Hi CatKiller, I followed your instructions, with some trepidation as I REALLY don't want to stuff up the kernel, but it worked like a charm. Quite simple in retrospect.
Thanks for your much appreciated help.
Carl.

---

