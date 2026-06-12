---
title: "hellahella install error, &quot;Installed distribution PasteScript 1.3.5 conflicts...&quot;"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by haroonie on 2007-08-05
Hello.

I'm trying to install hellahella for hellanzb and it spits out an error to me.  I've followed the guide here.. [http://freedomlinux.com/tags/hellahella](http://freedomlinux.com/tags/hellahella), and attempted to update Paste and Python to no avail.

Any suggestions please?  This is where the installer breaks.

> haroonie@haroonie-desktop:~/PasteScript$ sudo python ez_setup.py -U hellahella==dev
/usr/lib/python2.5/site-packages/setuptools/command/easy_install.py:173: UserWarning: Unbuilt egg for PasteScript [unknown version] (/home/haroonie/PasteScript)
  self.local_index = Environment(self.shadow_path+sys.path)
Searching for hellahella==dev
Reading [http://pythonpaste.org/package_index.html](http://pythonpaste.org/package_index.html)
Reading [http://pylons.groovie.org/project](http://pylons.groovie.org/project)
Reading [http://cheeseshop.python.org/pypi/hellahella/](http://cheeseshop.python.org/pypi/hellahella/)
Reading [http://hellanzb.com/trac/hellanzb/wiki/HellaHella](http://hellanzb.com/trac/hellanzb/wiki/HellaHella)
Reading [http://cheeseshop.python.org/pypi/hellahella/0.1](http://cheeseshop.python.org/pypi/hellahella/0.1)
Best match: hellahella dev
Downloading [http://hellanzb.com/hellanzb/hellahella/trunk#egg=hellahella-dev](http://hellanzb.com/hellanzb/hellahella/trunk#egg=hellahella-dev)
Doing subversion checkout from [http://hellanzb.com/hellanzb/hellahella/trunk](http://hellanzb.com/hellanzb/hellahella/trunk) to /tmp/easy_install-pBGVMu/trunk
Processing trunk
Running setup.py -q bdist_egg --dist-dir /tmp/easy_install-pBGVMu/trunk/egg-dist-tmp-1oFC4W
zip_safe flag not set; analyzing archive contents...
hellahella.config.environment: module references __file__
hellahella.config.routing: module references __file__
hellahella.tests.__init__: module references __file__
hellahella 0.1dev-r1086 is already the active version in easy-install.pth

Installed /usr/lib/python2.5/site-packages/hellahella-0.1dev_r1086-py2.5.egg
Processing dependencies for hellahella==0.1dev-r1086
error: Installed distribution PasteScript 1.3.5 conflicts with requirement PasteScript==dev,>=1.3.6dev-r6751
haroonie@haroonie-desktop:~/PasteScript$ 


Thanks.

---

### Post by Pragmatist on 2007-08-05
Please post this script: **ez_setup.py**

---

### Post by haroonie on 2007-08-05
> **Pragmatist said:**
> Please post this script: **ez_setup.py**

The ez_setup.py file has been attached.  Thanks.

---

### Post by Pragmatist on 2007-08-05
sudo python** ez_setup.py [COLOR=Blue]-U[/COLOR] **[COLOR=Red]**hellahella==dev**

[COLOR=Black]What is "hellahella==dev"?

On line 187 of the script you posted, it says this:
[/COLOR][/COLOR]> print '(Run "**ez_setup.py [COLOR=Blue]-U[/COLOR] [COLOR=Red]setuptools[/COLOR]**" to reinstall or upgrade.)'

Why not use "setuptools" as the argument instead of "hellahella==dev"??

---

### Post by haroonie on 2007-08-05
Thanks, I ran it with your suggestions and it worked, but i still have problems w/ other parts of setup.  here is after i ran setuptools...
```
haroonie@haroonie-desktop:~/PasteScript$ sudo python ez_setup.py -U setuptools/usr/lib/python2.5/site-packages/setuptools-0.6c6-py2.5.egg/setuptools/command/easy_install.py:173: UserWarning: Unbuilt egg for PasteScript [unknown version] (/home/haroonie/PasteScript)
  self.local_index = Environment(self.shadow_path+sys.path)
Searching for setuptools
Reading http://pythonpaste.org/package_index.html
Reading http://pylons.groovie.org/project
Reading http://cheeseshop.python.org/pypi/setuptools/
Reading http://cheeseshop.python.org/pypi/setuptools
Reading http://cheeseshop.python.org/pypi/setuptools/0.6c6
Best match: setuptools 0.6c6
Processing setuptools-0.6c6-py2.5.egg
setuptools 0.6c6 is already the active version in easy-install.pth
Installing easy_install script to /usr/bin
Installing easy_install-2.5 script to /usr/bin

Using /usr/lib/python2.5/site-packages/setuptools-0.6c6-py2.5.egg
Processing dependencies for setuptools
Finished processing dependencies for setuptools
haroonie@haroonie-desktop:~/PasteScript$ 

```
but with the next line of instructions via [http://freedomlinux.com/tags/hellahella](http://freedomlinux.com/tags/hellahella) running line "paster make-config hellahella hella.ini" i get errors.
```
haroonie@haroonie-desktop:~/PasteScript$ sudo paster make-config hellahella hella.ini
/usr/lib/python2.4/site-packages/paste/script/appinstall.py:202: UserWarning: Unbuilt egg for PasteScript [unknown version] (/home/haroonie/PasteScript)
  dist = pkg_resources.get_distribution(req)
Traceback (most recent call last):
  File "/usr/bin/paster", line 7, in ?
    sys.exit(
  File "/usr/lib/python2.4/site-packages/paste/script/command.py", line 76, in run
    invoke(command, command_name, options, args[1:])
  File "/usr/lib/python2.4/site-packages/paste/script/command.py", line 115, in invoke
    exit_code = runner.run(args)
  File "/usr/lib/python2.4/site-packages/paste/script/appinstall.py", line 64, in run
    return super(AbstractInstallCommand, self).run(new_args)
  File "/usr/lib/python2.4/site-packages/paste/script/command.py", line 210, in run
    result = self.command()
  File "/usr/lib/python2.4/site-packages/paste/script/appinstall.py", line 289, in command
    self.distro = self.get_distribution(self.requirement)
  File "/usr/lib/python2.4/site-packages/paste/script/appinstall.py", line 202, in get_distribution
    dist = pkg_resources.get_distribution(req)
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 229, in get_distribution
    if isinstance(dist,Requirement): dist = get_provider(dist)
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 115, in get_provider
    return working_set.find(moduleOrReq) or require(str(moduleOrReq))[0]
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 585, in require
    needed = self.resolve(parse_requirements(requirements))
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 487, in resolve
    raise VersionConflict(dist,req) # XXX put more info here
pkg_resources.VersionConflict: (PasteScript 1.1 (/usr/lib/python2.4/site-packages), Requirement.parse('PasteScript==dev,>=1.3.6dev-r6751'))
haroonie@haroonie-desktop:~/PasteScript$ 

```
seems as though it is looking for PasteScript 1.3.6dev again?

Thanks for the tips.

---

### Post by Pragmatist on 2007-08-06
I think your right.  You need to update your pastescript, or use a hack to trick the make-config into thinking you have the right version :)  This last choice is only good if you know that it really doesn't matter if you have the latest version.  I can explain how to do this if you want, but I recommend you first see if you can get a newer version.

---

### Post by haroonie on 2007-08-06
> **Pragmatist said:**
> I think your right.  You need to update your pastescript, or use a hack to trick the make-config into thinking you have the right version :)  This last choice is only good if you know that it really doesn't matter if you have the latest version.  I can explain how to do this if you want, but I recommend you first see if you can get a newer version.

i've updated, but it still seems its 1.3.5, i google'd and all i could find was this release [http://cheeseshop.python.org/pypi/PasteScript](http://cheeseshop.python.org/pypi/PasteScript) pointing to 1.3.5. The only reference i could find to pastescript 1.3.6dev-r6751 after searching is [http://wiki.pylonshq.com/display/pylonscookbook/Pylons+Execution+Analysis+0.9.6](http://wiki.pylonshq.com/display/pylonscookbook/Pylons+Execution+Analysis+0.9.6)

Can you help me with proper instructions to update to the needed version (1.3.6dev-r6751 or newer?) or even i can try the hack;)

its weird that i'm the only one having this error, that i know of... ?

Thanks for all your suggestions :)

---

### Post by Pragmatist on 2007-08-06
Before doing the hack, I just need some information:
Run this and wait for it to finish (it takes a few minutes)
```
sudo updatedb
```

Then type this and paste the output in your next post:
```
locate paster
```

---

### Post by miseryshining on 2007-08-07
you can upgrade PasteScript to the latest version with this command:

```
sudo easy_install -U PasteScript==dev

```

after that

```
sudo python ez_setup.py -U hellahella==dev

```

then follow the instructions from the hellahella website.

---

### Post by haroonie on 2007-08-18
> **miseryshining said:**
> you can upgrade PasteScript to the latest version with this command:

```
sudo easy_install -U PasteScript==dev

```

after that

```
sudo python ez_setup.py -U hellahella==dev

```

then follow the instructions from the hellahella website.

Thanks, worked great for me

---

### Post by BassKozz on 2007-11-20
I was having similar issues, and this thread fixed it for me... you'd think: [http://hellanzb.com/trac/hellanzb/wiki/HellaHella](http://hellanzb.com/trac/hellanzb/wiki/HellaHella)
Would have info on this... ohh, well, thanks to the community :)

---

