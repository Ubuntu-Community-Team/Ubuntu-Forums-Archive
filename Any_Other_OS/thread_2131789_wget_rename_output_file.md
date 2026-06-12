---
title: "wget rename output file"
date: 2013-04-02
forum: Any Other OS
---

### Post by Si1414 on 2013-04-02
I am using wget in Cygwin to download some files. The wget code and a sample url are shown below:

```
wget -i slist.txt -r -l1 -p
```

```
http://www.website.com/file?_ob=MRL&_cid=271352&_user=1022551&_pii=S0924424705006436&_check=y&_origin=browsee&_zone=rslt_list_item&_coverDate=2006-05-24&wchp=dGLbVlk-zSkWz&md5=6088a053f5b5f75f8a7b973da6e32d45&pid=1-s2.0-S0924424705006436-file.pdf 

```

By default the name of the output pdf file is set to whatever the download link is. For example, for the above sample, the saved pdf filename is: "file@_ob=MRL&_cid=271352&_user=1022551&_pii=S0924424705006436&_check=y&_origin=browsee&_zone=rslt_list_item&_coverDate=2006-05-24&wchp=dGLbVlk-zSkWz&md5=6088a053f5b5f75f8a7b973da6e32d45&pid=**1-s2.0-S0924424705006436-file.pdf**"

As you can see the filename is too long and sometimes it does not save the pdf file because it is too long. 
Therefore, I want to specify the output filename. I want it to be automatically changed to the bold string (above). That means whatever left after "pid=".
For example for this case, the output filename would be "**1-s2.0-S0924424705006436-file.pdf**"

I want to include this in the wget command, since for some files, since the length of the filename is too long, it can not save it on the hard disk.

Thank you for your help.

---

### Post by papibe on 2013-04-02
Hi Si1414.

I do several downloads that way. What I do is to use a little  bash scripting to read every line so I can use wget's -O option to rename the output:
```
#!/bin/bash

while read -r link
do
        output="${link##*pid=}"

        echo wget "$link" -O "$output"

done < ./slist.txt
```
Note that in this example I'm not actually downloading, but just echoing the command. Try it, and when you feel comfortable remove the word **echo**.

If the files are fairly big, or you have an not-so-stable connections, I would also advice to use a cycle in case 'wget' fails:
```
#!/bin/bash

while read -r link
do
        output="${link##*pid=}"

        echo wget -c "$link" -O "$output"
        until [ $? = 0 ]
        do
                echo wget -c "$link" -O "$output"
        done

done < ./slist.txt
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Si1414 on 2013-04-03
Thank you papibe for your great help.
The first code works perfect, however, the second one seems stay in the loop and not save the file. However, the first one solved my problem.


In the same concept, if the output filename is:


"**99284351.pdf**@tp=&filename=1284351&indexfile=68896"


I want to save the output file to:
"**99284351.pdf**"
This means whatever is left after ".pdf" should be removed.


How to modify the first code you sent to perform this?


Thank you for your help.

---

### Post by papibe on 2013-04-04
> **Si1414 said:**
> "**99284351.pdf**@tp=&filename=1284351&indexfile=68896"

I want to save the output file to:
"**99284351.pdf**"

In the previous expression:
```
output="${link##*pid=}"
```
'##' that means remove the biggest match for '*pid=' from the beginning.

In order to remove from the end, use '%%'. For example:
```
output="${link%%.pdf*}"
```
However, since even '.pdf' is getting removed, you need to add it back. This should work:
```
output="${link%%.pdf*}".pdf
```
Note that this would work if all urls have the same format. If you have a mix of the first case and the second one, it would be necessary to add more code to test for each case.

Does that help? Let us know how it goes.
Regards.

---

### Post by Si1414 on 2013-04-04
Thank you papibe again for your help. However, it seems that I have a problem here. I am using the following code:

```
while read -r link
do
        output="${link%%.pdf*}".pdf
        wget -nc -r -l1 -p "$link" -O "$output"
done < ./ilist2.txt

```

It gives the following warning:
*"WARNING: combining -O with -r or -p will mean that all downloaded content will be placed in the single file you specified."*


I need to use *-r -l1 -p* to download, because each links inside "ilist2.txt" does not contain only the address to a single *pdf *file. But, they also contain other addresses, such as *gif* and *jsp *files as well. That is why I use *-r -l1 -p *to download all of them. I delete *gif *and *jsp *files later and keep the *pdf *file. 

However, it seems that I can not use that method anymore, because of the -O command.

To solve the above problem, if I can filter the *pdf *URL, I think the problem would be solved. That means, wget only downloads one URL which is the *pdf *URL and not the *gif *and *jsp *files.
The *pdf *URLs have the "**pdf**" word in common, which might be useful for filtration. For example, a sample link is:

```
http://amazon.com/temp3/35/569018/**99284351.pdf**@tp=&filename=1284351&indexfile=68896
```

I am wondering if it is possible to place the above filter for the wget inside the *while loop*? In that case, wget opens each link inside ilist2.txt and search for the *pdf* URL inside it and downloads only that *pdf* file and saves it with -O command, and then opens the next link inside ilist2.txt, and searches for the pdf file and so on.

Thank you very much indeed again for your help.

---

### Post by papibe on 2013-04-04
You could filter the lines containing 'pdf' outside the loop:
```
#!/bin/bash
while read -r link
do
        http_strip="${link##*/}"
        output="${http_strip%%.pdf*}".pdf

        echo wget -c "$link" -O "$output"

done **< <(grep \.pdf ./slist.txt)**
```
That would work for addresses formated as the second example.

Let us know how it goes.
Regards.

---

### Post by Si1414 on 2013-04-05
Thank You very much papibe for your help.

---

