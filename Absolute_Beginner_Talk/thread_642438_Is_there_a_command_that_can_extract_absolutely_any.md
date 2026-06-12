---
title: "Is there a command that can extract absolutely anything? .cab, .exe .tgz .whatever"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by climatewarrior on 2007-12-16
Is there anything that can extract absolutely anything? And if not what can extract the most kind of files. And what cant that extract?

---

### Post by PinkFloyd102489 on 2007-12-16
Under GNOME, if you right-click on the package and click Extract Here, it'll handle just about anything.

---

### Post by kerry_s on 2007-12-16
for the command line i use "unp" (sudo apt-get install unp), to unpack just type> unp whatever <and it will unpack, it has unpacked everything i've thrown at it and will tell you if your missing the unpacker needed, it will tell you the exact name so you can just apt-get what you need for it to unpack it. it's lightweight and fast.

---

### Post by climatewarrior on 2007-12-16
The problem is that I'm writing a program that downloads a ton of drivers from the internet and unpacks them and the problem is that they all have very different compression formats. unp seems like a nice solution but I don't know if I really want to add an extra dependency to the program.

---

### Post by thelatinist on 2007-12-16
Why not just have your program use the usual commands for the different formats (tar xvfz for tgz, tar xvfj for tar.bz2, etc.)?

---

### Post by climatewarrior on 2007-12-16
Yeah I guess I could do that but I just wanted to check if there was a simpler way.

---

### Post by Majorix on 2007-12-16
Fastest way is the native way. As with C, it may be harder to use, but it is the fastest. If you are downloading tons of .cabs .tgz's etc in your program, then you want it to be as fast as possible.

So put short, use the default extractor for each type.

---

### Post by climatewarrior on 2007-12-16
Yes I will use the different extractors then. But for .exe's what is best cabextract or unzip?

Also is there a way I can use find in the command line when I dont know the exact file name

For example right now if I want to look for something what I so is finf -name "filename" 
but what if I dont know the exact name of the file, how can I look for it using find or another command?

Thanks Guys

---

### Post by climatewarrior on 2007-12-19
Can you guys please checkout if this code is right

```

        if ".exe" or ".zip" in URL:
		decompression = "unzip "
	elif ".tar" in URL:
		decompression = "tar -vvf "	
	elif ".gz" in URL:
		decompression = "tar -xvvzf "
	elif ".bz2" in URL:
		decomproession = "tar --bzip2 "
	elif ".cab" in URL:
		decopmpression = "cabextract "
	elif ".rar" in URL:
		decompression = "unrar "

```

---

### Post by macogw on 2007-12-19
> **climatewarrior said:**
> Can you guys please checkout if this code is right

```

        if ".exe" or ".zip" in URL:
		decompression = "unzip "
	elif ".tar" in URL:
		decompression = "tar -vvf "	
	elif ".gz" in URL:
		decompression = "tar -xvvzf "
	elif ".bz2" in URL:
		decomproession = "tar --bzip2 "
	elif ".cab" in URL:
		decopmpression = "cabextract "
	elif ".rar" in URL:
		decompression = "unrar "

```

If you want it to be fast, get rid of the vv's in the tar and gz ones.  Also, I'd probably do
```

elif ".tar.bz2" in URL:
    decompression = "tar -xjf
elif ".tar" in URL:
    decompression = "tar -xf"

```
-xf works with both .tar and .tar.gz just fine, and j is the tar option for bzip2'd files.  You can also use "bunzip2" to decompress (but not untar, I don't think) things ending in .bz2

---

