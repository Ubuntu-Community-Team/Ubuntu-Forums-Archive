---
title: "Building Flightgear from cvs sources"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-18
Been trying to build Flightgear from sources in order to try and get a specific plane working

Followed the instructions [here]("http://www.flightgear.org/cvs/anoncvs.html")

But got no executable after running make.

Any chance someone could take a look at my make output errors from terminal and suggest where I might be going wrong?

```

user@ubuntu:~/myprogs/cvs/FlightGear-0.9/source$ sudo make
Making all in tests
make[1]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/tests'
if gcc -DHAVE_CONFIG_H -I. -I. -I../src/Include   -I/usr/local/include  -g -O2 -D_REENTRANT -MT al-info.o -MD -MP -MF ".deps/al-info.Tpo" -c -o al-info.o al-info.c; \
        then mv -f ".deps/al-info.Tpo" ".deps/al-info.Po"; else rm -f ".deps/al-info.Tpo"; exit 1; fi
al-info.c:8:20: error: AL/al.h: No such file or directory
al-info.c:9:21: error: AL/alc.h: No such file or directory
al-info.c:11:24: error: AL/alext.h: No such file or directory
al-info.c:20:26: error: AL/altypes.h: No such file or directory
al-info.c:21:27: error: AL/alctypes.h: No such file or directory
al-info.c: In function &#8216;main&#8217;:
al-info.c:29: error: &#8216;ALCint&#8217; undeclared (first use in this function)
al-info.c:29: error: (Each undeclared identifier is reported only once
al-info.c:29: error: for each function it appears in.)
al-info.c:29: error: expected &#8216;;&#8217; before &#8216;i&#8217;
al-info.c:30: error: expected &#8216;;&#8217; before &#8216;data&#8217;
al-info.c:31: error: &#8216;ALCdevice&#8217; undeclared (first use in this function)
al-info.c:31: error: &#8216;device&#8217; undeclared (first use in this function)
al-info.c:32: error: &#8216;ALCcontext&#8217; undeclared (first use in this function)
al-info.c:32: error: &#8216;context&#8217; undeclared (first use in this function)
al-info.c:34: error: &#8216;ALCenum&#8217; undeclared (first use in this function)
al-info.c:34: error: expected &#8216;;&#8217; before &#8216;error&#8217;
al-info.c:50: error: &#8216;AL_VENDOR&#8217; undeclared (first use in this function)
al-info.c:50: warning: assignment makes pointer from integer without a cast
al-info.c:53: error: &#8216;AL_RENDERER&#8217; undeclared (first use in this function)
al-info.c:53: warning: assignment makes pointer from integer without a cast
al-info.c:56: error: &#8216;AL_VERSION&#8217; undeclared (first use in this function)
al-info.c:56: warning: assignment makes pointer from integer without a cast
al-info.c:59: error: &#8216;AL_EXTENSIONS&#8217; undeclared (first use in this function)
al-info.c:59: warning: assignment makes pointer from integer without a cast
al-info.c:65: error: &#8216;AL_TRUE&#8217; undeclared (first use in this function)
al-info.c:67: error: &#8216;ALC_DEVICE_SPECIFIER&#8217; undeclared (first use in this function)
al-info.c:67: warning: assignment makes pointer from integer without a cast
al-info.c:71: error: &#8216;ALC_MAJOR_VERSION&#8217; undeclared (first use in this function)
al-info.c:71: error: &#8216;data&#8217; undeclared (first use in this function)
al-info.c:73: error: &#8216;ALC_MINOR_VERSION&#8217; undeclared (first use in this function)
al-info.c:76: error: &#8216;ALC_EXTENSIONS&#8217; undeclared (first use in this function)
al-info.c:76: warning: assignment makes pointer from integer without a cast
al-info.c:79: error: &#8216;error&#8217; undeclared (first use in this function)
al-info.c:85: error: &#8216;ALC_DEFAULT_DEVICE_SPECIFIER&#8217; undeclared (first use in this function)
al-info.c:85: warning: assignment makes pointer from integer without a cast
make[1]: *** [al-info.o] Error 1
make[1]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/tests'
make: *** [all-recursive] Error 1
user@ubuntu:~/myprogs/cvs/FlightGear-0.9/source$ 


```note that it does say,

> 
If you are building FlightGear from CVS,        you need the CVS version of SimGear
Well I looked in synaptic & saw SimGear is in there, but whether I have the *correct* version I dunno.. where would I get "the CVS version of SimGear" if that's likely to be the problem?

[edit]

aaaahh.. [http://www.simgear.org/](http://www.simgear.org/) simple as that

simgear wouldn't ./configure until I installed openAL through synaptic.. ties in with the errors I was getting;

Ack, still no joy:

```

user@ubuntu:~/myprogs/cvs/FlightGear-0.9/source$ sudo make
Making all in tests
make[1]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/tests'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/tests'
Making all in man
make[1]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/man'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/man'
Making all in scripts
make[1]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts'
Making all in debug
make[2]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts/debug'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts/debug'
Making all in perl
make[2]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts/perl'
Making all in examples
make[3]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts/perl/examples'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts/perl/examples'
make[3]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts/perl'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts/perl'
make[2]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts/perl'
Making all in python
make[2]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts/python'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts/python'
make[2]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts'
make[1]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/scripts'
Making all in src
make[1]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/src'
Making all in Include
make[2]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/src/Include'
make  all-am
make[3]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/src/Include'
make[3]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/src/Include'
make[2]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/src/Include'
Making all in Aircraft
make[2]: Entering directory `/home/user/myprogs/cvs/FlightGear-0.9/source/src/Aircraft'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../src/Include -I../.. -I../../src  -I/usr/local/include  -g -O2 -D_REENTRANT -MT aircraft.o -MD -MP -MF ".deps/aircraft.Tpo" -c -o aircraft.o aircraft.cxx; \
        then mv -f ".deps/aircraft.Tpo" ".deps/aircraft.Po"; else rm -f ".deps/aircraft.Tpo"; exit 1; fi
In file included from aircraft.cxx:41:
../../src/Cockpit/panel.hxx:37:23: error: osg/ref_ptr: No such file or directory
../../src/Cockpit/panel.hxx:38:24: error: osg/StateSet: No such file or directory
../../src/Cockpit/panel.hxx:39:25: error: osg/Texture2D: No such file or directory
In file included from ../../src/Cockpit/panel.hxx:54,
                 from aircraft.cxx:41:
../../src/Input/input.hxx:38:43: error: simgear/structure/SGBinding.hxx: No such file or directory
../../src/Input/input.hxx:41:50: error: simgear/scene/util/SGSceneUserData.hxx: No such file or directory
In file included from aircraft.cxx:42:
../../src/Cockpit/hud.hxx:49:21: error: osg/State: No such file or directory
In file included from ../../src/FDM/flight.hxx:93,
                 from ../../src/Aircraft/aircraft.hxx:35,
                 from ../../src/Cockpit/hud.hxx:55,
                 from aircraft.cxx:42:
../../src/FDM/groundcache.hxx:29:39: error: simgear/math/SGGeometry.hxx: No such file or directory
In file included from aircraft.cxx:44:
../../src/Model/acmodel.hxx:20:21: error: osg/Group: No such file or directory
../../src/Model/acmodel.hxx:21:22: error: osg/Switch: No such file or directory
../../src/Input/input.hxx:164: error: &#8216;SGBinding&#8217; was not declared in this scope
../../src/Input/input.hxx:164: error: template argument 1 is invalid
../../src/Input/input.hxx:164: error: template argument 1 is invalid
../../src/Input/input.hxx:164: error: template argument 2 is invalid
../../src/Input/input.hxx:335: error: &#8216;SGPickCallback&#8217; was not declared in this scope
../../src/Input/input.hxx:335: error: template argument 1 is invalid
../../src/Input/input.hxx:335: error: template argument 1 is invalid
../../src/Input/input.hxx:335: error: template argument 2 is invalid
../../src/Input/input.hxx:335: error: template argument 2 is invalid
../../src/Input/input.hxx:335: error: template argument 4 is invalid
../../src/Cockpit/panel.hxx:78: error: ISO C++ forbids declaration of &#8216;Texture2D&#8217; with no type
../../src/Cockpit/panel.hxx:78: error: invalid use of &#8216;::&#8217;
../../src/Cockpit/panel.hxx:78: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../../src/Cockpit/panel.hxx:80: error: &#8216;ref_ptr&#8217; is not a member of &#8216;osg&#8217;
../../src/Cockpit/panel.hxx:80: error: &#8216;ref_ptr&#8217; is not a member of &#8216;osg&#8217;
../../src/Cockpit/panel.hxx:80: error: &#8216;Texture2D&#8217; is not a member of &#8216;osg&#8217;
../../src/Cockpit/panel.hxx:80: error: template argument 2 is invalid
../../src/Cockpit/panel.hxx:80: error: template argument 4 is invalid
../../src/Cockpit/panel.hxx:80: error: expected unqualified-id before &#8216;>&#8217; token
../../src/Cockpit/panel.hxx:103: error: ISO C++ forbids declaration of &#8216;StateSet&#8217; with no type
../../src/Cockpit/panel.hxx:103: error: invalid use of &#8216;::&#8217;
../../src/Cockpit/panel.hxx:103: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../../src/Cockpit/panel.hxx:117: error: ISO C++ forbids declaration of &#8216;ref_ptr&#8217; with no type
../../src/Cockpit/panel.hxx:117: error: invalid use of &#8216;::&#8217;
../../src/Cockpit/panel.hxx:117: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
../../src/Cockpit/panel.hxx:147: error: &#8216;osg::State&#8217; has not been declared
../../src/Cockpit/panel.hxx:149: error: &#8216;osg::State&#8217; has not been declared
../../src/Cockpit/panel.hxx:150: error: &#8216;osg::State&#8217; has not been declared
../../src/Cockpit/panel.hxx:158: error: &#8216;osg::Texture2D&#8217; has not been declared
../../src/Cockpit/panel.hxx:161: error: &#8216;osg::Texture2D&#8217; has not been declared
../../src/Cockpit/panel.hxx:215: error: ISO C++ forbids declaration of &#8216;ref_ptr&#8217; with no type
../../src/Cockpit/panel.hxx:215: error: invalid use of &#8216;::&#8217;
../../src/Cockpit/panel.hxx:215: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
../../src/Cockpit/panel.hxx:216: error: ISO C++ forbids declaration of &#8216;ref_ptr&#8217; with no type
../../src/Cockpit/panel.hxx:216: error: invalid use of &#8216;::&#8217;
../../src/Cockpit/panel.hxx:216: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
../../src/Cockpit/panel.hxx:253: error: &#8216;SGBinding&#8217; has not been declared
../../src/Cockpit/panel.hxx:274: error: &#8216;SGBinding&#8217; was not declared in this scope
../../src/Cockpit/panel.hxx:274: error: template argument 1 is invalid
../../src/Cockpit/panel.hxx:274: error: template argument 2 is invalid
../../src/Cockpit/panel.hxx:342: error: &#8216;osg::State&#8217; has not been declared
../../src/Cockpit/panel.hxx:384: error: &#8216;osg::State&#8217; has not been declared
../../src/Cockpit/panel.hxx:385: error: &#8216;osg::State&#8217; has not been declared
../../src/Cockpit/panel.hxx:421: error: &#8216;osg::State&#8217; has not been declared
../../src/Cockpit/panel.hxx:451: error: &#8216;osg::State&#8217; has not been declared
../../src/Cockpit/panel.hxx:470: error: &#8216;osg::State&#8217; has not been declared
../../src/Cockpit/panel.hxx:492: error: &#8216;osg::State&#8217; has not been declared
../../src/Cockpit/panel.hxx:547: error: &#8216;osg::State&#8217; has not been declared
../../src/Cockpit/panel.hxx:583: error: &#8216;osg::State&#8217; has not been declared
../../src/FDM/groundcache.hxx:90: error: &#8216;SGTriangled&#8217; does not name a type
../../src/FDM/groundcache.hxx:91: error: &#8216;SGSphered&#8217; does not name a type
../../src/FDM/groundcache.hxx:154: error: &#8216;SGTriangled&#8217; has not been declared
../../src/FDM/groundcache.hxx:155: error: &#8216;SGSphered&#8217; has not been declared
../../src/Cockpit/hud.hxx:739: warning: &#8216;fgUpdateHUD&#8217; initialized and declared &#8216;extern&#8217;
../../src/Cockpit/hud.hxx:739: error: variable or field &#8216;fgUpdateHUD&#8217; declared void
../../src/Cockpit/hud.hxx:739: error: &#8216;State&#8217; is not a member of &#8216;osg&#8217;
../../src/Cockpit/hud.hxx:739: error: expected primary-expression before &#8216;)&#8217; token
../../src/Cockpit/hud.hxx:740: warning: &#8216;fgUpdateHUD&#8217; initialized and declared &#8216;extern&#8217;
../../src/Cockpit/hud.hxx:740: error: variable or field &#8216;fgUpdateHUD&#8217; declared void
../../src/Cockpit/hud.hxx:740: error: redefinition of &#8216;int fgUpdateHUD&#8217;
../../src/Cockpit/hud.hxx:739: error: &#8216;int fgUpdateHUD&#8217; previously defined here
../../src/Cockpit/hud.hxx:740: error: &#8216;State&#8217; is not a member of &#8216;osg&#8217;
../../src/Cockpit/hud.hxx:740: error: expected primary-expression before &#8216;,&#8217; token
../../src/Cockpit/hud.hxx:740: error: expected primary-expression before &#8216;x_start&#8217;
../../src/Cockpit/hud.hxx:740: error: expected primary-expression before &#8216;y_start&#8217;
../../src/Cockpit/hud.hxx:741: error: expected primary-expression before &#8216;x_end&#8217;
../../src/Cockpit/hud.hxx:741: error: expected primary-expression before &#8216;y_end&#8217;
../../src/Model/acmodel.hxx:47: error: ISO C++ forbids declaration of &#8216;ref_ptr&#8217; with no type
../../src/Model/acmodel.hxx:47: error: invalid use of &#8216;::&#8217;
../../src/Model/acmodel.hxx:47: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
../../src/Model/acmodel.hxx: In member function &#8216;void FGAircraftModel::select(bool)&#8217;:
../../src/Model/acmodel.hxx:42: error: &#8216;_selector&#8217; was not declared in this scope
make[2]: *** [aircraft.o] Error 1
make[2]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/src/Aircraft'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/myprogs/cvs/FlightGear-0.9/source/src'
make: *** [all-recursive] Error 1

```now it's really a mess :(

The problems still seem to kick off after it starts making mention of simgear. I'm pretty lost now though, anyone with a clue please do sing out thanks.

I'm now wondering if I should actually be here > [http://www.simgear.org/cvs.html](http://www.simgear.org/cvs.html)

Can't seem to follow it without running into errors all over the place; I'm certain I'm doing something basically wrong here :( help!

---

