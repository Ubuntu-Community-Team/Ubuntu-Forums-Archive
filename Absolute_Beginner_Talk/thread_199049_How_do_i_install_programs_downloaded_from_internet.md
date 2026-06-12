---
title: "How do i: install programs downloaded from internet"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by falkenberg_cph on 2006-06-18
Yes. How do I install programs downloaded from the internet.
I have the folder unpacked on my desktop. What is the next step?

Carsten

---

### Post by u.b.u.n.t.u on 2006-06-18
Make sure there is an uninstall script included. I installed something and it wrecked ubuntu.  It didn't work and I had to manually delete many files. I have since reinstalled ubuntu due in part to that.

Synaptic is the safest.

---

### Post by falkenberg_cph on 2006-06-18
Ok, always make sure i can uninstall (how do i do that - im new to this).

In this case it is PyKaraoke which apparently is not included in synaptics.
So how is the general procedure for terminal installations.

---

### Post by aysiu on 2006-06-18
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) is a good place to start in general.

Your program's README file says: > INSTALLATION (LINUX, SOURCE INSTALLS)

PyKaraoke requires the following libraries to be installed:

 * Python ([www.python.org](www.python.org))
 * Pygame ([www.pygame.org](www.pygame.org))
 * WxPython ([www.wxpython.org](www.wxpython.org))
 * Numeric python module (numpy.sourceforge.net)

If these libraries are not already installed on your system, you can
download them from the websites listed.

Linux users may find these packages are available directly from their
distro's package manager.

Gentoo users can install all prerequisites using:
	# emerge python pygame wxGTK wxpython numeric

Debian users can install all prerequisites using:
	# apt-get install python python-pygame libwxgtk-python python-numeric

With the prerequisites installed, unzip the release and run the following
as root:

# python setup.py install

This installs the executables into /usr/bin, and you can then run
PyKaraoke from anywhere using "pykaraoke".

Alternatively you can run PyKaraoke without installing by simply
unzipping and running "python pykaraoke.py" from the unzip location. So I would listen and try: ```
cd ~/Desktop/pykaraoke-0.4.1
sudo aptitude update
sudo aptitude install python python-pygame libwxgtk-python python-numeric
sudo python setup.py install
```

---

