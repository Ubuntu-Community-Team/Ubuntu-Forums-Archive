---
title: "Compilers install"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by SuperTeece on 2007-01-11
So I want to write some simple code and complile but it appears gcc is not installed by default. After searching the forums I found a thread describing how to install using a sudo command, but trying this failed because I have no way of connecting that computer to the internet.

My question is this: where can I download the build-essential package manually and how do I go about installing it.

Thanks in advance for the help!:)

---

### Post by Qrk on 2007-01-11
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to download the packages from another computer.

Note that because build-essential is a meta package, you can't just download it. You'll need to choose each .deb you need separately. Just download each package listed as a dependency here

[http://packages.ubuntu.com/edgy/devel/build-essential](http://packages.ubuntu.com/edgy/devel/build-essential)

To install, just double click.

---

### Post by kj1h234lkj1234 on 2007-01-11
Or you can just select "build-essential" from Applications -> Add/Remove Programs

Or type the following into your Applications -> Accessories -> Terminal:

```
aptitude install build-essential
```Aptitude handles metapackages just fine.

To remove:

```
aptitude remove build-essential
```

---

### Post by SuperTeece on 2007-01-11
> **Qrk said:**
> Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to download the packages from another computer.

Note that because build-essential is a meta package, you can't just download it. You'll need to choose each .deb you need separately. Just download each package listed as a dependency here

[http://packages.ubuntu.com/edgy/devel/build-essential](http://packages.ubuntu.com/edgy/devel/build-essential)

To install, just double click.

This sounds like what I was looking for. I am using 6.06 so I need Dapper packages correct?

---

### Post by Tomosaur on 2007-01-11
> **kj1h234lkj1234 said:**
> Or you can just select "build-essential" from Applications -> Add/Remove Programs

Or type the following into your Applications -> Accessories -> Terminal:

```
aptitude install build-essential
```Aptitude handles metapackages just fine.

To remove:

```
aptitude remove build-essential
```

Yeah, but this installs the packages. He wants to move them to a comp with no net access.

There's a way to download packages without installing them. To do this, type:
```

sudo apt-get -d build-essential

```

I'm not sure where they get downloaded to though.

---

### Post by SuperTeece on 2007-01-11
> **kj1h234lkj1234 said:**
> Or you can just select "build-essential" from Applications -> Add/Remove Programs

Or type the following into your Applications -> Accessories -> Terminal:

```
aptitude install build-essential
```Aptitude handles metapackages just fine.

To remove:

```
aptitude remove build-essential
```


I can't do this because lack of internet connection. I tried just to make sure before posting this request for help.

---

### Post by IYY on 2007-01-11
> I can't do this because lack of internet connection. I tried just to make sure before posting this request for help.

You can if the CD is inserted. The Build Essential package is on the CD repositories, just not installed by default.

---

### Post by SuperTeece on 2007-01-11
> **IYY said:**
> You can if the CD is inserted. The Build Essential package is on the CD repositories, just not installed by default.


Ok, I put the CD back in and found the magnificant package manager. This worked beautifully and I have to admit I feel horrible for not trying this first. I'm accustom to other distro installations that ask what packages are to be installed before installation begins.

Thanks for all of the help.

---

