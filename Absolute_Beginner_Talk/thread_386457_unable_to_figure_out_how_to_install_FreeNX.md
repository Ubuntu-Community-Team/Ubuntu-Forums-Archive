---
title: "unable to figure out how to install FreeNX"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-03-17
Saw a post on Digg earlier in the week about remot desktops and thought that it would be neat.  When attempting to install FreeNX I get the following:

[B]brian@brian-desktop:~$ sudo apt-get install freenx
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

The following packages have unmet dependencies:[/B]
 [B] freenx: Depends: nxagent (>= 1.4.92+1.5.0) but it is not installable
E: Broken packages
[/B]

could it be that I don't have the repositories installed correctly?  Or could it be not compatabile with a 64 bit Ubuntu?  Or is it just because I really  have no idea what I am doing?

Any help would be great!!

-B

---

### Post by ajmorris on 2007-03-17
> **marmaladejackson said:**
> Saw a post on Digg earlier in the week about remot desktops and thought that it would be neat.  When attempting to install FreeNX I get the following:

[B]brian@brian-desktop:~$ sudo apt-get install freenx
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

The following packages have unmet dependencies:[/B]
 [B] freenx: Depends: nxagent (>= 1.4.92+1.5.0) but it is not installable
E: Broken packages
[/B]

could it be that I don't have the repositories installed correctly?  Or could it be not compatabile with a 64 bit Ubuntu?  Or is it just because I really  have no idea what I am doing?

Any help would be great!!

-B

run ```
sudo apt-get update
``` then install nxagent, then try to install freenx again.

---

### Post by marmaladejackson on 2007-03-17
OK... did that.  Terminal tells me that nxagent is not avalible:

[B]brian@brian-desktop:~$ sudo apt-get install nxagent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nxagent is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nxlibs-dev
E: Package nxagent has no installation candidate
brian@brian-desktop:~$ [/B]


I found a pakage in synaptic called nxagent-dev, but it won't let me install it either:

[B]nxagent-dev:
 Depends: nxagent (>=1.4.92+1.5.0-11ubuntu1) but it is not installable
[/B]

Does that help any?

-B

---

### Post by hkfczrqj on 2007-04-16
Hello, 

I have a very similar problem with FreeNX 0.6.0 on Feisty (amd64), using the repository at dentalonline.com to get the freenx packages.

```
# apt-get install freenx
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
  freenx: Depends: nxagent (>= 2.1.0) but it is not installable
E: Broken packages
```

Then, if I try to install nxagent I get

```
# apt-get install nxagent
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package nxagent is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nxlibs-dev
E: Package nxagent has no installation candidate

```

Any ideas on what might be wrong?

Thanks

---

