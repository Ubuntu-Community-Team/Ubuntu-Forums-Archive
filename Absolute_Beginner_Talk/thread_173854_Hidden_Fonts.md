---
title: "Hidden Fonts"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-05-11
Are there such things as hidden fonts? When I was tying a document in Open Office. I selected the text and typed in "Verdana", a common Windows font. However, the text changed. However, Verdana was not on the list. What is going on? Thanks!

---

### Post by nanotube on 2006-05-11
when a font is not installed, and you type it in, openoffice selects another font that is "closest" to the one you typed in. (at least that's my understanding of how this works). so it selected some other font "behind the scenes".

---

### Post by Clay85 on 2006-05-11
This is like sci-fi. I'm scared. 

Hold me?

---

### Post by Nikusan on 2006-05-11
[QUOTE=amitroy5]Are there such things as hidden fonts? When I was tying a document in Open Office. I selected the text and typed in "Verdana", a common Windows font. However, the text changed. However, Verdana was not on the list. What is going on? Thanks![/QUOTE]

If nanotube is right and you don't have the common windows fonts installed, you can install the msttcorefonts package. It will give you verdana, times, etc.

---

### Post by amitroy5 on 2006-05-11
How do I install the msttcorefonts? I ran "sudo apt-get install msttcorefonts", but it cannot seem to find the package. I do want the Windows fonts. How should I proceed? Thanks!

---

### Post by Nikusan on 2006-05-11
[QUOTE=amitroy5]How do I install the msttcorefonts? I ran "sudo apt-get install msttcorefonts", but it cannot seem to find the package. I do want the Windows fonts. How should I proceed? Thanks![/QUOTE]

That's the right command, but I think the package is in multiverse. [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by amitroy5 on 2006-05-11
What Repositories should I add? I checked them all, and I am not sure which one to add.

---

### Post by nanotube on 2006-05-11
well, if you go to the first link in my sig, and go to the sources.list section, you can get my sources.list, and replace yours with it. (it is located in /etc/apt/sources.list).
then run
```
sudo apt-get update
```
and then
```
sudo apt-get install msttcorefonts
```

or you can open up synaptic, hit reload, and search for "fonts" and see if one of the packages that comes up is msttcorefonts, and install it.

---

