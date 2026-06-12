---
title: "How to check for dependencies"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by tmafcerqueira on 2006-08-21
When I download a .deb package that I cannot find in the repositories sometimes I'm unable to run it after the installation because of it's dependencies. How do I check for dependencies?
Thanks

---

### Post by Klaidas on 2006-08-21
I fyou can't find the packagke in Ubuntus repos, a website that hosts your packege should porovide information on what the .deb depends.

---

### Post by Perfect Storm on 2006-08-21
Just remember to enable universe/multiverse in your sourcelist. The .deb you're downloading might have dependencies which require universe/multiverse package. (also check if the application is there instead of downloading the .deb seperatly, it's saver that way).

---

### Post by visik7 on 2006-08-21
dpkg -i package.deb
apt-get -f install

---

### Post by tmafcerqueira on 2006-08-22
I think I have the universe/multiverse enabled, but I'm not sure. I can't have any international repositories because my ISP has trafic limitations, and the limit for international traffic is very low. The portuguese universities have, however, repositories that I can use.
As to the apt-get -f install... This installs the dependencies?
Thanks

---

### Post by az on 2006-08-22
You should never download a deb file. 

You should use a package manager to install packages and the dependencies are resolved for you at the same time.  Use apt-get, aptitude, synaptic, add-remove programs, whatever...

---

### Post by tmafcerqueira on 2006-08-23
I wish I could do so but sometimes the programs are not on the repositories:(

---

### Post by christhemonkey on 2006-08-23
If you double click the .deb,
the gdebi package installer will say in big red writing:
"Error Dependency not met: blaaaa-dev > 1.2"

And if it doesnt then its dependencies are met.

---

### Post by az on 2006-08-23
> **tmafcerqueira said:**
> I wish I could do so but sometimes the programs are not on the repositories:(


They should be made available in a third-party repo, then.  

I would question the wisdom of installing an individual deb which is not provided with the required dependencies in it's own repo.

Anyway, it is good practice to avoid non-ubuntu packages anyway.

---

### Post by tmafcerqueira on 2006-08-27
Thanks for the help;)

---

### Post by BlackBaron1024 on 2008-07-04
You can use

```
dpkg --info package.deb
```

That will give all the info available from the package, including its dependencies.

Cheers!

P.S. I know this is an old post, but someone (like me) may come here looking for an answer.

---

