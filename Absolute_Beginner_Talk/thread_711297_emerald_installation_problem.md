---
title: "emerald installation problem"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by rimi on 2008-02-29
Hi Everybody,
                  I tried to install emerald on my ubuntu gutsy, It shows the following problem
sudo apt-get install emerald
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
  emerald: Depends: libemeraldengine0 but it is not going to be installed
E: Broken packages

Can anybody help me regarding this. I tried with synaptic package manager but it shows some libwnck dependency. When I check it, it is already there. I do not know what is happening.

Please help

Thanks in advance
rimi:KS

---

### Post by dondad on 2008-02-29
> **rimi said:**
> Hi Everybody,
                  I tried to install emerald on my ubuntu gutsy, It shows the following problem
sudo apt-get install emerald
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
  emerald: Depends: libemeraldengine0 but it is not going to be installed
E: Broken packages

Can anybody help me regarding this. I tried with synaptic package manager but it shows some libwnck dependency. When I check it, it is already there. I do not know what is happening.

Please help

Thanks in advance
rimi:KS

Try filtering for broken packages in synaptic. If it finds any let it try to fix them and go from there.

---

