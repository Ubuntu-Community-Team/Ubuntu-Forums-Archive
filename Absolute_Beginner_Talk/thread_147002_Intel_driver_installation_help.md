---
title: "Intel driver installation help"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by gdoyel on 2006-03-19
So it's come down that I should update my video card driver, and I set out to do it.

I have an Intel Thinkpad R52, so my card is **Mobile Intel 915GM/GMS,910GML Express**.

I go to Intel's website, find the driver, download it. It's a .tar.gz. I extract, and following the readme, I'm supposed to rpm it. I know Ubuntu doesn't use rpm, so I get alien to do the job. The only problem now is that I can't seem to find the .rpm file anywhere, even by using the search feature in GNOME.

Any experience, help, anything?

---

### Post by taurus on 2006-03-19
If you use an alien to convert rpm to deb, then you can install it with
```

sudo dpkg -i filename.deb

```
Why need the rpm file again???

---

### Post by gdoyel on 2006-03-19
[QUOTE=taurus]If you use an alien to convert rpm to deb, then you can install it with
```

sudo dpkg -i filename.deb

```
Why need the rpm file again???[/QUOTE]

Can't even find the initial .rpm!

I'm trying XFree86 from their website direct.

---

### Post by taurus on 2006-03-19
Well, you need to know where you have downloaded it!!!  If not sure, run this command from the prompt,
```

sudo find / -name *.rpm -print

```

---

