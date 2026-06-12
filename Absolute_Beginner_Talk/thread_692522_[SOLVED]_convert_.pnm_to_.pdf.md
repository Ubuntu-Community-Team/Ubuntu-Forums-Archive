---
title: "[SOLVED] convert .pnm to .pdf"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by jryprt on 2008-02-09
I scanned 406 pages with XSane they were saved as .pnm how can I convert them   
 to .pdf or something for windows to read (for others with windows I will burn to cd for windows user) I know gimp will but I want to convert all at the same time (as a batch)

---

### Post by asmoore82 on 2008-02-09
the netpbm package!
```
sudo apt-get install netpbm
```

... will get it installed,
but running it is command line only, making it perfect for batch processing;
something like:

```
for pic in *.pnm
do
  pnmtojpeg "${pic}" > "${pic}-converted.jpg"
done
```

---

### Post by jryprt on 2008-02-09
> **asmoore82 said:**
> the netpbm package!
```
sudo apt-get install netpbm
```

... will get it installed,
but running it is command line only, making it perfect for batch processing;
something like:

```
for pic in *.pnm
do
  pnmtojpeg "${pic}" > "${pic}-converted.jpg"
done
```

WOW way over my head , OK I have the file in /jerry/multipageproject1 
the scans are   image-0001.pnm  to image-0406.pnm  can you give me a idea how I will try.

---

### Post by asmoore82 on 2008-02-09
> **jryprt said:**
> WOW way over my head , OK I have the file in /jerry/multipageproject1 
the scans are   image-0001.pnm  to image-0406.pnm  can you give me a idea how I will try.
in a terminal("System->Accessories->Terminal"),
run the 1st command to update your package lists(you will need to be online),
run the 2nd command to install netpbm(you will need to be online),
just `cd` (**change directory**) to the location with the pics,
and type in the long-ish `for` loop command, pressing enter at the end of each line,
the `for` loop won't actually do anthing until you type the final `done` and press enter:

```
sudo apt-get update
sudo apt-get install netpbm
cd /jerry/multipageproject1
for pic in *.pnm
do pnmtojpeg "${pic}" > "${pic}-converted.jpg"
done
```

after that finishes, it may spit out >400 lines of "converting image..."
all of the original image-*.pnm files will still be there,
along with new image-*.png-converted.jpg files to match.

---

### Post by jryprt on 2008-02-09
> **asmoore82 said:**
> in a terminal("System->Accessories->Terminal"),
run the 1st command to update your package lists(you will need to be online),
run the 2nd command to install netpbm(you will need to be online),
just `cd` (**change directory**) to the location with the pics,
and type in the long-ish `for` loop command, pressing enter at the end of each line,
the `for` loop won't actually do anthing until you type the final `done` and press enter:

```
sudo apt-get update
sudo apt-get install netpbm
cd /jerry/multipageproject1
for pic in *.pnm
do pnmtojpeg "${pic}" > "${pic}-converted.jpg"
done
```

after that finishes, it may spit out >400 lines of "converting image..."
all of the original image-*.pnm files will still be there,
along with new image-*.png-converted.jpg files to match.

I did that and after I did done hit enter got this ```
pnmtojpeg: *.pnm - No such file or directory

```
so I tried again  know I get this```
jerry@jerry-desktop:~$ cd /jerry/multipageproject1
bash: cd: /jerry/multipageproject1: No such file or directory
jerry@jerry-desktop:~$ 

```
screenshot shows they are in /jerry/multipageproject1

---

### Post by asmoore82 on 2008-02-09
I think I know where they are...

"jerry" seems to be your home folder, which would actually be /home/jerry

so try running the `cd` command line like this:```
cd /home/jerry/multipageproject1
```
if the `cd` was successful, the **[B]"~"**[/B] part of the prompt should change to reflect the new location,
then hit "UP" a few times until you see the `for` loop command and hit enter to re-run it.

---

### Post by jryprt on 2008-02-09
> **asmoore82 said:**
> I think I know where they are...

"jerry" seems to be your home folder, which would actually be /home/jerry

so try running the `cd` command line like this:```
cd /home/jerry/multipageproject1
```
if the `cd` was successful, the **[B]"~"**[/B] part of the prompt should change to
reflect the new location, then hit "UP" a few times until you see the `for` loop command
and hit enter to re-run it.
That did it , Now I have .pnm & .jpeg side by side is there a way to get rid of the .pnm all at the same time .[COLOR="Red"](GOT IT)[/COLOR]

---

### Post by asmoore82 on 2008-02-09
cool ...
I would get rid of the pnm files graphically:
right-click on whitespace in the folder,
select "Arrange Items -> By Type"
and then highlight and delete the pnm's.

the terminal command would be:```
mv *.pnm ~/.Trash
```

don't forget to empty the trash if you need the disk space back.

---

### Post by jryprt on 2008-02-09
> **asmoore82 said:**
> cool ...
I would get rid of the pnm files graphically:
right-click on whitespace in the folder,
select "Arrange Items -> By Type"
and then highlight and delete the pnm's.

the terminal command would be:```
mv *.pnm ~/.Trash
```

don't forget to empty the trash if you need the disk space back.

Just what I did. Thank You

---

