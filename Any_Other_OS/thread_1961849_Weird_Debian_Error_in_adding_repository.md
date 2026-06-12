---
title: "Weird Debian Error in adding repository"
date: 2012-04-20
forum: Any Other OS
---

### Post by Ryupower on 2012-04-20
Hey guys, I've been experimenting with Linux mint Debian Edition, and I must say, despite some rough edges here and there, it's been an ok ride. I have this weird error when adding an apt line. No clue what's going on here, but I thought it'd be good not to mess with the lines until I have some more experienced user's opinion. OK, here it goes:

[B]
Command:[/B] sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn

**Result:**


Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 65, in <module>
    if not sp.add_source_from_line(line):
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 630, in add_source_from_line
    (deb_line, file) = expand_ppa_line(line.strip(), self.distro.codename)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 47, in expand_ppa_line
    sourceslistd = apt_pkg.Config.find_dir("Dir::Etc::sourceparts")
AttributeError: 'module' object has no attribute 'Config'

---

### Post by jefsview on 2012-04-20
First off, you are trying to add an Ubuntu PPA to a Debian system -- their binaries are not 100% compatible and you will break your system!

If you're looking for the latest and greatest Gimp, then use the repos for Unstable (Sid) or Debian Experimental. If you wish to stay on testing, you can still poach from Sid or Experimental by using apt-pining. If you don't, then you'll hit dependancy hell.

If you still wish to use the PPA from launchpad, you need to edit out anything referring to Ubuntu in the address. And the easiest way to edit add it would be to edit your /etc/apt/sources.list.

-- Jeff

---

### Post by Ryupower on 2012-04-20
> **jefsview said:**
> First off, you are trying to add an Ubuntu PPA to a Debian system -- their binaries are not 100% compatible and you will break your system!

If you're looking for the latest and greatest Gimp, then use the repos for Unstable (Sid) or Debian Experimental. If you wish to stay on testing, you can still poach from Sid or Experimental by using apt-pining. If you don't, then you'll hit dependancy hell.

If you still wish to use the PPA from launchpad, you need to edit out anything referring to Ubuntu in the address. And the easiest way to edit add it would be to edit your /etc/apt/sources.list.

-- Jeff

Can't find the sid repos for the gimp. So far I didn't have any problems with ubuntu packages, tbh. (then again, I don't take those that change anything to the system)

---

### Post by Ryupower on 2012-04-20
EDIT: Problem solved, had to disable and reactivate the repositories. Used the synaptic package manager to add the repository. The new gimp is up and running without a problem.

Still I heard there was a newer version in some Sid repository (2.7.5 or 2.8 )...

(ps thanks for your help! )

---

### Post by jefsview on 2012-04-21
That would be debian-multimedia-unstable and the same for experimental, which has those. There's a web page that lists what in those repos from the main Debian site.

-- Jeff

---

