---
title: "Making a .bin?"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-10-10
You all know sun's Java packages that are in .bin? Does anyone know how to make a .bin that you can create your own output to the terminal then extract a folder?

---

### Post by taurus on 2006-10-10
You can convert .bin to .iso and mount it...  There is a program called bin2iso and after you convert it, mount it with

```

sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.iso /mnt/iso
cd /mnt/iso
ls -la

```

---

### Post by Ben Sprinkle on 2006-10-10
I don't mean bin as in a image. I mean a .bin that holds like an archive like the Java .bin that sends output upon executed. I know all about the cd images mate. ;)

---

### Post by insineratehymn on 2006-10-10
I think we need a little bit more information on what you are trying to do.

Are you wanting to make a binary or a shell script?
A shell script (like a batch file) is something you can use to run terminal commands, and you could even call a java program in them.

---

### Post by Ben Sprinkle on 2006-10-10
I know that.
Just go download the java 1.5.0_09 bin and you will see what I am talking about.

---

### Post by meng on 2006-10-10
> **Goat Spirit said:**
> I know that.
Just go download the java 1.5.0_09 bin and you will see what I am talking about.
*Chuckle* "Just go download a 15MB file and see what I'm talking about." Ahem. What insinerate was saying was that you could likely achieve what you wanted to do with a shell script. Except that we can't be sure because you don't want to tell more precisely what you're trying to do. Are we going to continue going round in circles trying to second-guess each other?

---

### Post by jwd45244 on 2006-10-10
> **Goat Spirit said:**
> I know that.
Just go download the java 1.5.0_09 bin and you will see what I am talking about.

You have to understand that extensions in Linux don't mean anything (Unlike Windows).  The file you are referring to is a self-extracting archive.  So there is nothing magical about the ".bin" part of the name.  What exactly are you trying to do?

---

### Post by Ben Sprinkle on 2006-10-10
Make a self extracting archive that sends output to the user via the terminal. I don't want them to be able to open with ark or something like that.

---

### Post by Ben Sprinkle on 2006-10-10
Ooo, I just looked and it's a shell script. That's how it's sending output. It also creates some sfx.exe when extracting. Anyone know how to do this?

EDIT: [http://linux.org.mt/article/selfextract](http://linux.org.mt/article/selfextract)
Found it.

---

