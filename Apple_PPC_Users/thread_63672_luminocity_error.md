---
title: "luminocity error"
date: 2005-09-08
forum: Apple PPC Users
---

### Post by open_flax on 2005-09-08
hello 
i wont install luminocity and i follow step by step ubuntu howto luminocity:

[https://wiki.ubuntu.com/LuminocityHowTo?highlight=%28luminocity%29](https://wiki.ubuntu.com/LuminocityHowTo?highlight=%28luminocity%29)
 but when get a comand:
 jhbuild -f luminocity/jhbuildrc-luminocity build xserver luminocity
 
i get back  a error:


bash: /home/flaz/luminocity/bin/jhbuild: /usr/bin/env: bad interpreter: Permission denied
 So i wont resolve this problem

---

### Post by alsimoes on 2005-09-22
I have a similar problem

```
andre@ubuntu:~/luminocity$ ~/bin/jhbuild -f ~/luminocity/jhbuildrc-luminocity build xserver luminocity
Traceback (most recent call last):
  File "/home/andre/bin/jhbuild", line 6, in ?
    jhbuild.main.main(sys.argv[1:])
  File "/home/andre/luminocity/jhbuild/jhbuild/main.py", line 115, in main
    jhbuild.commands.run(command, config, args)
  File "/home/andre/luminocity/jhbuild/jhbuild/commands/base.py", line 44, in run
    return func(config, args)
  File "/home/andre/luminocity/jhbuild/jhbuild/commands/base.py", line 120, in do_build
    module_set = jhbuild.moduleset.load(config)
  File "/home/andre/luminocity/jhbuild/jhbuild/moduleset.py", line 175, in load
    ms.modules.update(_parse_module_set(config, uri).modules)
  File "/home/andre/luminocity/jhbuild/jhbuild/moduleset.py", line 183, in _parse_module_set
    document = xml.dom.minidom.parse(filename)
  File "/usr/lib/python2.4/site-packages/_xmlplus/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.4/site-packages/_xmlplus/dom/expatbuilder.py", line 924, in parse
    fp = open(file, 'rb')
IOError: [Errno 2] No such file or directory: '/home/andre/luminocity/jhbuild/jhbuild/../modulesets/luminocity.modules'
andre@ubuntu:~/luminocity$

```

---

