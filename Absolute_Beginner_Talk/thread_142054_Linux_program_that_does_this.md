---
title: "Linux program that does this?"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by arachn1d on 2006-03-09
Is there a linux program that does sequential image downloading?

Enter image path 1 = /images/1.jpg
Enter image path 2 = /images/25.jpg

and it downloads 1->25?

Also, is there a linux program that uploads images to an image hosting site?

Thanks

---

### Post by JShadow on 2006-03-09
From the wget man page:

> wget -r -l1 --no-parent -A.jpg [http://www.server.com/dir/](http://www.server.com/dir/)

---

### Post by Klejs on 2006-03-09
You can use the wget command to download all the pictures in an folder
on an webserver, but not all servers agree to this.

Read the manual for wget by typing **man wget** in an terminal

Hope you will get it working, and for the upload I dont have any tips, sry...:(

---

### Post by IYY on 2006-03-09
[QUOTE=arachn1d]Is there a linux program that does sequential image downloading?

Enter image path 1 = /images/1.jpg
Enter image path 2 = /images/25.jpg

and it downloads 1->25?

Also, is there a linux program that uploads images to an image hosting site?

Thanks[/QUOTE]

This can be done with a quick shell script:

```

#!/bin/sh

for (( x = $2; x <= $3; x++))
do
        wget $1/$x\.jpg
done

```

Save this in a file named, for example download.sh

Then to download images 1...5 from [www.site.com](www.site.com) just run: 

./download.sh [www.site.com](www.site.com) 1 5

---

