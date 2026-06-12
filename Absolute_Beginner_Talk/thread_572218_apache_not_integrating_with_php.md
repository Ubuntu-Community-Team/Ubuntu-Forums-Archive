---
title: "apache not integrating with php"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by vinu76jsr on 2007-10-10
I installed apache php and mysql on my feisty following the instruction on how to forge 
but it required me to install apache module for php but it gives following error
```
root@vrindavan:/home/vaibhav# apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: apache2-mpm-prefork (> 2.0.52) but it is not going to be installed or
                                apache2-mpm-itk but it is not going to be installed
E: Broken packages

```
please helpme out

---

### Post by Kilz on 2007-10-10
> **vinu76jsr said:**
> I installed apache php and mysql on my feisty following the instruction on how to forge 
but it required me to install apache module for php but it gives following error
```
root@vrindavan:/home/vaibhav# apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: apache2-mpm-prefork (> 2.0.52) but it is not going to be installed or
                                apache2-mpm-itk but it is not going to be installed
E: Broken packages

```
please helpme out

This command will try to resolve issues. Let it remove what it wants to.
```
sudo apt-get install -f
```

[Next go here and use this howto]("https://help.ubuntu.com/community/ApacheMySQLPHP"). You are always safer using Ubuntu documentation with ubuntu

---

### Post by vinu76jsr on 2007-10-10
I hav installed webmin and it replace apache-mpn-worker or something 
can u throw some light

---

