---
title: "Tool to find duplicate photos with different names?"
date: 2007-10-08
forum: Art &amp; Design
---

### Post by Tsu Dho Nimh on 2007-10-08
After a hard drive accident, I have multiple copies of recovered photos on a large hard drive ... thousands of photos in dozens of directories. Because many of them were recovered by multiple passes of multiple disk recovery tools, the same photo has a different name in each recovery pass and the create times might be different.

Is there a tool that can find possible duplicates by something besides the create time, file size, and name and show them to me so I can delete or keep all but one?

---

### Post by ac7ss on 2007-10-08
GQview will do this. It can find similar and identical files.

---

### Post by rsambuca on 2007-10-08
You can also just search for *.jpg and then sort the results by size.  At least all the copies will be grouped together in the list so you can delete the unwanted ones.

---

### Post by Madpilot on 2007-10-09
gThumb can do this.

Applications->Graphics-> gThumb Image Viewer, then Edit->Search For Duplicates

---

### Post by Tsu Dho Nimh on 2007-10-09
Thanks. 

I'll try gThumb and see if it can handle that many files.

---

### Post by Endolith on 2007-12-15
FSlint will find files that are exact duplicates, but the interface is not so good and you have to click each one by hand, instead of selecting an entire directory to clean out.

---

### Post by hyperboimmv on 2007-12-22
fdupes 

sudo apt-get install fdupes

After it is installed, sudo fdupes -r ./stuff > /whereyouwant/log/dupes.txt and it will create a list of duplicates it finds. It uses md5 hashes to find the duplicates.

---

### Post by Filippo on 2008-08-31
suppose you have a lot of pictures in /home/filippo/Photos/
make the directory /home/filippo/duplicates/

```

fdupes -r -f -1 /home/filippo/Photos/ > /home/filippo/Photos/duplicates.txt

cat /home/filippo/Photos/duplicates.txt | xargs  mv -f --target-directory /home/filippo/duplicates/


```

this works, but not conserve directory structure in duplicates.

---

### Post by john_spiral on 2008-10-23
> **Filippo said:**
> 
```

fdupes -r -f -1 /home/filippo/Photos/ > /home/filippo/Photos/duplicates.txt

cat /home/filippo/Photos/duplicates.txt | xargs  mv -f --target-directory /home/filippo/duplicates/


```


Thanks for the above command Filippo.

Does anyone know how to recreate the folder structure with the "xargs  mv -f --target-directory ...." command. 

The duplicates.txt file might have duplicate/quadruplicate files with the same name on the same line, for example:

/home/john/Pictures/Zac\ most/New\ Zac/IMG_0276.JPG /home/john/Pictures/recent\ all/IMG_0276.JPG 

John

---

### Post by gaston1982 on 2009-10-19
I recently read this thread. Maybe it's too late now, but the command to preserve the parent directories is 
cat duplicates.txt | xargs -i cp --parents {} /home/filippo/duplicates
Then you can delete duplicates with
cat duplicates.txt | xargs rm

---

### Post by knezmej on 2011-12-14
@ac7ss: "GQview will do this. It can find similar and identical files."
  Thank You!
Geeqie (gqview) is great.

---

