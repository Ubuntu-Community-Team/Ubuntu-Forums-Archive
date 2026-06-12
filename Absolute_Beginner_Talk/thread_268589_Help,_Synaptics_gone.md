---
title: "Help, Synaptics gone"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by limitedmage on 2006-09-30
Hi,

I've got a real problem now. :-? My sources list got corrupted and the terminal kept telling me to run "apt-get install -f". I did that, and now Synaptic is gone! I tried to use "apt-get install synaptic" but the following appears:

```

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  synaptic: Depends: libapt-pkg-libc6.3-6-3.10
            Depends: libvte4 (>= 1:0.11.11) but it is not going to be installed
E: Broken packages

```

How can I fix this?

EDIT:

Terminal is gone as well!!! (thank god I installed Konsole as well)
I get this when using "apt-get install gnome-terminal":

```

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  synaptic: Depends: libapt-pkg-libc6.3-6-3.10
            Depends: libvte4 (>= 1:0.11.11) but it is not going to be installed
E: Broken packages

```

---

### Post by petri on 2006-09-30
Did you "apt-get install ...! without **sudo**?

You have ubuntu? Don't install Konsole that's Kubuntus terminal.

Always use **aptitude** not apt-get. Always update first like this

```
sudo aptitude update
sudo aptitude install *program-name*
```

---

