---
title: "tk8.4.16 installation problem"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by nanxy85 on 2008-02-19
hello, im new with ubuntu and i need to install tcl/tk8.4.16. i manage to install tcl8.4.16 but having problem for tk8.4.16 as below:

/root/tk8.4.16/unix/../generic/tk3d.c:1279: error: ‘TkBorder’ has no member named ‘resourceRefCount’
/root/tk8.4.16/unix/../generic/tk3d.c:1280: error: ‘Tk_FakeWin’ has no member named ‘display’
/root/tk8.4.16/unix/../generic/tk3d.c:1280: error: ‘Tk_FakeWin’ has no member named ‘screenNum’
/root/tk8.4.16/unix/../generic/tk3d.c:1280: error: ‘TkBorder’ has no member named ‘screen’
/root/tk8.4.16/unix/../generic/tk3d.c:1281: error: ‘Tk_FakeWin’ has no member named ‘atts’
/root/tk8.4.16/unix/../generic/tk3d.c:1281: error: ‘TkBorder’ has no member named ‘colormap’
/root/tk8.4.16/unix/../generic/tk3d.c:1301: error: ‘TkDisplay’ has no member named ‘borderTable’
/root/tk8.4.16/unix/../generic/tk3d.c:1301: error: ‘TkDisplay’ has no member named ‘borderTable’
/root/tk8.4.16/unix/../generic/tk3d.c:1306: error: ‘TkBorder’ has no member named ‘nextPtr’
/root/tk8.4.16/unix/../generic/tk3d.c:1307: error: ‘Tk_FakeWin’ has no member named ‘display’
/root/tk8.4.16/unix/../generic/tk3d.c:1307: error: ‘Tk_FakeWin’ has no member named ‘screenNum’
/root/tk8.4.16/unix/../generic/tk3d.c:1307: error: ‘TkBorder’ has no member named ‘screen’
/root/tk8.4.16/unix/../generic/tk3d.c:1308: error: ‘Tk_FakeWin’ has no member named ‘atts’
/root/tk8.4.16/unix/../generic/tk3d.c:1308: error: ‘TkBorder’ has no member named ‘colormap’
/root/tk8.4.16/unix/../generic/tk3d.c:1311: error: ‘TkBorder’ has no member named ‘objRefCount’
/root/tk8.4.16/unix/../generic/tk3d.c: In function ‘TkDebugBorder’:
/root/tk8.4.16/unix/../generic/tk3d.c:1391: error: ‘TkWindow’ has no member named ‘dispPtr’
/root/tk8.4.16/unix/../generic/tk3d.c:1394: error: ‘TkDisplay’ has no member named ‘borderTable’
/root/tk8.4.16/unix/../generic/tk3d.c:1394: error: ‘TkDisplay’ has no member named ‘borderTable’
/root/tk8.4.16/unix/../generic/tk3d.c:1400: error: ‘TkBorder’ has no member named ‘nextPtr’
/root/tk8.4.16/unix/../generic/tk3d.c:1403: error: ‘TkBorder’ has no member named ‘resourceRefCount’
/root/tk8.4.16/unix/../generic/tk3d.c:1405: error: ‘TkBorder’ has no member named ‘objRefCount’
make: *** [tk3d.o] Error 1



please anyone help me.....im desperate:confused:

---

### Post by jan quark on 2008-02-20
did you try to install both apps through synaptic?
I think they are both in the repositories.

---

### Post by falldog7 on 2008-02-21
you should install libx11-dev
$sudo apt-get install libx11-dev
:)

---

### Post by nanxy85 on 2008-02-25
i try to install the libx11-dev but it shown a broken package as below

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
  libx11-dev: Depends: libx11-6 (= 2:1.0.0-0ubuntu9.1) but 2:1.1.1-1ubuntu4 is to be installed

              Depends: libxau-dev but it is not going to be installed
              Depends: libxdmcp-dev but it is not going to be installed
E: Broken packages





so,i try to install it from the synaptic but it show that the other dependencies cannot be install...like below

libx11-dev:
  Depends: libx11-6 (=2:1.0.0-0ubuntu9.1) but 2:1.1.1-1ubuntu4 is to be installed
 Depends: libxau-dev but it is not going to be installed
 Depends: libxdmcp-dev but it is not going to be installed


by the way i try to install the tcl/tk just by using the synatic...it actually didt work out...alot of dependencies and mistake got to do with the library and all....i blur......:confused:

---

### Post by jjrp78 on 2008-03-01
I had the same problem you have and after installing the libx11-dev it worked like a charm. May be you should start another thread about how havinv problems to install libx11-dev

---

### Post by Rophy on 2008-03-27
thanxxxx JJ u r magnifcinet

---

