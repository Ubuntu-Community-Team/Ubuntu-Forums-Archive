---
title: "wget download specific links"
date: 2013-04-30
forum: Any Other OS
---

### Post by Si1414 on 2013-04-30
Hello,

I am using wget to download some pdf files. However, it seems that there is a problem. I am using the following code:
```

while read -r link
do
        http_strip="${link##*/}"
        output="${http_strip%%.pdf*}".pdf
        wget -nc --no-parent -c "$link" -O "$output"
done < <(grep \.pdf ./ilist.txt)

```
The *ilist.txt* contains the address of pages which contain pdf files. The links in the *ilist.txt* are like the following:
```
http://amazon.com/shelf/145.12/book.58616/pdf
```

I am trying to download the pdf file which is embedded in the above webpage. The direct link to that file is as follows:
```
http://amazon.com/shelf/145.12/book.58616/check/58616_ftp.pdf?s=1&k=hg4523nx&440f11f6
```

and I want to save the above file to "*58616_ftp.pdf*".

I have the links in *ilist.txt* and not the direct links, that is why I am using those links in *ilist.txt* and not the direct links.

However, after running the above code for a sample page, a "*pdf.pdf*" file is saved which is a corrupted file (The size is 12k and I can not open it).
So, the problem is, it does not save the actual file, and second problem is the filename is "*pdf.pdf*", which should be "*58616_ftp.pdf*".

Please let me know if you have any suggestions.
I am using Cygwin on Windows.

Thank you for your help.

---

