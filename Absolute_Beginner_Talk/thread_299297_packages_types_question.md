---
title: "packages types question"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by MaximusDM on 2006-11-13
Hi.
I'm new to linux and just started using ubuntu dapper drake.
I've been looking for several hours to get things straight, everything kind of smooth but I haven't figure it out why some packages are not updated by apt-get, I mean, I found out the format of a line in sources.list and found also that the number after the version of the package (m#ubuntu#n) is the nth version of ubuntu based on the mth version of debian, am I right?
But I have a question that I wasn't able to find out. I can see the full path for packages using a web browser, my doubt is why can I get some of them using apt-get update and not others, cause when I use the apt-cache search for one that I saw there beffore, near another one wich I can get, I don't have it.

Does my text makes sense?

I'll give an example:
from this link
    [http://archive.ubuntu.com/ubuntu/pool/universe/o/opencv/](http://archive.ubuntu.com/ubuntu/pool/universe/o/opencv/)
I use
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
I can't get any of the opencv, I assume it's cause there's no deb package
but I don't know why I only get the opencv-doc_0.9.6-4.1build1_all.deb since there are two more opencv-doc and one of them with a newer version.

Other thing, from the same source (deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe)
I can get kdevelop3 packages but not the ones from kdevelop any idea why?

I already tried other distributions in the source, other than dapper, but as I've seen in other places, other dist have different components, right?
For instance breezy has free, non-free.

Sorry for the long post.
But the real thing that I couldn't figure out yet is why can I get some packs and not others in same path.

Thanks for your time.

Oh, by the way, I'm using kubuntu.

---

### Post by seshomaru samma on 2006-11-13
I'm not I understand your question but if you check out your sources list it might answer it
```
gedit /etc/apt/sources.list
```

---

### Post by Marsolin on 2006-11-14
For the opencv issue, you are correct that the lack of a deb file of that name is the reason nothing shows up. For opencv-doc you only see one version because it is the only one associated with the Dapper release. 0.9.7-3ubuntu1 is currently available for Edgy and Feisty.

Regarding your second example, kdevelop3 is the name used for the Dapper release, and while it still exists for the Edgy and Feisty versions, all it does is install kdevelop. While using Dapper, kdevelop3 is what you want to use.

---

### Post by MaximusDM on 2006-11-14
Thanks.
But how can I tell wich release is associated with a given package?
I've tried reading the dsc file but I can't take that info out of it.
One more question, is there any info about the package compatibility with other releases besides the one it is meant to? Also, same question about compatibility between ubuntu and debian packages.
The reason I'm asking is for instance if I install an edgy(or other release) package in dapper, how can I know beforehand if it will work or not?
Thanks again.

---

### Post by Marsolin on 2006-11-14
The detailed answer is to look in [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/), pick the one you want, then navigate the sections until you find the Packages.bz2 or Packages.gz file. It contains the list that Synaptic uses for a particular section and architecture.

The easy way is searching the [http://packages.ubuntu.com/](http://packages.ubuntu.com/) page.

---

### Post by MaximusDM on 2006-11-14
Thanks a lot.
That's a bookmark candidate. :)

---

