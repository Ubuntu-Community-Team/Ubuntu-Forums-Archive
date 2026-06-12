---
title: "That amazing kde digital clock"
date: 2009-01-24
forum: Art &amp; Design
---

### Post by butlins on 2009-01-24
I installed kubuntu many moons ago,
but have not yet found out how to 
disply the digital clock (see screenie)

-help

---

### Post by eightmillion on 2009-01-24
> **butlins said:**
> I installed kubuntu many moons ago,
but have not yet found out how to 
disply the digital clock (see screenie)

-help

That's the train clock plasmoid. You have to get it from the KDE source repository. If you have svn and the appropriate dev packages installed, you should be able to do this:

```
svn co svn://anonsvn.kde.org/home/kde/trunk/playground/base/plasma/applets/train-clock/
cd train-clock
mkdir build && cd build
cmake .. -DCMAKE_INSTALL_PREFIX=`kde-config --prefix`
make
sudo make install
```

---

### Post by butlins on 2009-01-24
Thanks for the fast reply
will get to work installing :popcorn:

---

### Post by pcpinkerton on 2009-03-17
> **eightmillion said:**
> That's the train clock plasmoid. You have to get it from the KDE source repository. If you have svn and the appropriate dev packages installed, you should be able to do this:

```
svn co svn://anonsvn.kde.org/home/kde/trunk/playground/base/plasma/applets/train-clock/
cd train-clock
mkdir build && cd build
cmake .. -DCMAKE_INSTALL_PREFIX=`kde-config --prefix`
make
sudo make install
```

Almost but not quite got an error:

$ cmake .. -DCMAKE_INSTALL_PREFIX=`kde-config --prefix`
CMake Error at CMakeLists.txt:7 (kde4_add_ui_files):                                                              
  Unknown CMake command "kde4_add_ui_files".                                                                      


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more    
  information run "cmake --help-policy CMP0000".                             
This warning is for project developers.  Use -Wno-dev to suppress it.        

-- Configuring incomplete, errors occurred!

---

### Post by eightmillion on 2009-03-18
> **pcpinkerton said:**
> Almost but not quite got an error:

$ cmake .. -DCMAKE_INSTALL_PREFIX=`kde-config --prefix`
CMake Error at CMakeLists.txt:7 (kde4_add_ui_files):                                                              
  Unknown CMake command "kde4_add_ui_files".                                                                      


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more    
  information run "cmake --help-policy CMP0000".                             
This warning is for project developers.  Use -Wno-dev to suppress it.        

-- Configuring incomplete, errors occurred!

This plasmoid is apparently not so easy to build if you aren't building the whole tree. Try replacing CMakeLists.txt with the file I've attached. Then just run:
```

cmake -DCMAKE_INSTALL_PREFIX=`kde-config --prefix`
make
sudo make install

```
in the train-clock directory. Don't worry about making the build directory.

---

### Post by So Tough on 2009-03-20
Is this called a binary? and if so then do binaries aventually become easier to install or stay binaries forever?

---

### Post by t4p on 2010-05-12
I am still unable to build this clock. I had same error as user pcpinkerton and did what user eightmillion suggested (including file he provided). 
For his first command, I am getting the following:
```
CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/milovan/.kde/share/apps;/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:7 (find_package)


-- Configuring incomplete, errors occurred!

```
Any idea what is a problem?
Using Kubuntu 10.04

---

