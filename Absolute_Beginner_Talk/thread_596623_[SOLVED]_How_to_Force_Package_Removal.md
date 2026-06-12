---
title: "[SOLVED] How to Force Package Removal"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Odd-rationale on 2007-10-29
Hello! I have a very annoying problem with the msttcorefonts package.

When I tried to install it, I received an error message saying that there is an error in the package. Here is the terminal output:

```
Setting up msttcorefonts (2.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--18:46:07--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... failed: Connection timed out.
--18:46:17--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving internap.dl.sourceforge.net... ^[^[failed: Connection timed out.
--18:46:27--  http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... failed: Connection timed out.
--18:46:37--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
--18:46:47--  http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving superb-west.dl.sourceforge.net... failed: Connection timed out.
--18:46:57--  http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving superb-east.dl.sourceforge.net... failed: Connection timed out.
--18:47:07--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--18:47:17--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
--18:47:27--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
--18:47:37--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
--18:47:47--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
--18:47:57--  http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving umn.dl.sourceforge.net... failed: Connection timed out.
--18:48:07--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I had this problem before, and I tried the launchpad ([https://answers.launchpad.net/ubuntu/+question/15835](https://answers.launchpad.net/ubuntu/+question/15835)) but since none of the suggestions worked, I ended up reinstalling my system.

Now, some weeks later, I tried to install a package that had msttcorefonts as a dependency and having the same problem. I really do NOT want to do another system install.

The real problem is that anything that I try to do that uses apt-get will make it try to install msttcorefonts again - which takes a long time.

So ideally, I would like to have msttcorefonts installed. But I would be quite happy to just have it completely removed.

Your help is greatly appreciated.

---

### Post by overdrank on 2007-10-29
> **Odd-rationale said:**
> Hello! I have a very annoying problem with the msttcorefonts package.

When I tried to install it, I received an error message saying that there is an error in the package. Here is the terminal output:

```
Setting up msttcorefonts (2.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--18:46:07--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... failed: Connection timed out.
--18:46:17--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving internap.dl.sourceforge.net... ^[^[failed: Connection timed out.
--18:46:27--  http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... failed: Connection timed out.
--18:46:37--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
--18:46:47--  http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving superb-west.dl.sourceforge.net... failed: Connection timed out.
--18:46:57--  http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving superb-east.dl.sourceforge.net... failed: Connection timed out.
--18:47:07--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--18:47:17--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
--18:47:27--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
--18:47:37--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
--18:47:47--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
--18:47:57--  http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving umn.dl.sourceforge.net... failed: Connection timed out.
--18:48:07--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I had this problem before, and I tried the launchpad ([https://answers.launchpad.net/ubuntu/+question/15835](https://answers.launchpad.net/ubuntu/+question/15835)) but since none of the suggestions worked, I ended up reinstalling my system.

Now, some weeks later, I tried to install a package that had msttcorefonts as a dependency and having the same problem. I really do NOT want to do another system install.

The real problem is that anything that I try to do that uses apt-get will make it try to install msttcorefonts again - which takes a long time.

So ideally, I would like to have msttcorefonts installed. But I would be quite happy to just have it completely removed.

Your help is greatly appreciated.

Hi and maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=579916](http://ubuntuforums.org/showthread.php?t=579916)
Good luck!

---

### Post by Gazneth on 2007-10-29
I don't know how to fix your problem, but the msttcorefonts package is available in the standard ubuntu repositories, maybe you could try disabling your sourceforge repos and installing the package from the standard repos.

---

### Post by Odd-rationale on 2007-10-29
Still not working. I believe I am installing from the standard repositories.

Neither apt-get or aptitude works to purge or remove the package.

Note: I was able to install it in Feisty just fine.

---

### Post by Odd-rationale on 2007-10-30
Hey It's working now! I have no idea what I did to make it work. But thanks anyways everybody!!!

---

