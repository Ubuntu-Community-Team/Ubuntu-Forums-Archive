---
title: "maxwell for maya"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by antonyant11 on 2008-03-07
Hi I need a hand installing maxwell for maya on linux 64. I have the files but am having trouble completing the step 2.


Maxwell Plug-ins for Maya 8.0, 8.5 and 2008 for Linux-x64
=========================================================

There are two steps for installing the plug-in, copying files and setting up the environment.

1.-Copy files:

You must have root privileges to copy files into Maya installation folders.

$MAYA_HOME is the installation path of Maya, normally:
/usr/aw/maya8.0-x64 for Maya 8.0-x64, 
/usr/autodesk/maya8.5-x64 for Maya 8.5-x64, 
/usr/autodesk/maya2008-x64 for Maya 2008-x64. 

Copy the contents (10 files) of to_maya_scripts_others to $MAYA_HOME/scripts/others 
Copy the contents (2 files)of to_maya_scripts_AETemplates to $MAYA_HOME/scripts/AETemplates 
Copy the contents (5 files)of to_maya_icons to $MAYA_HOME/icons 
Copy the contents (1 file)of to_maya_bin_plug-ins_rendererDesc to $MAYA_HOME/bin/plug-ins/rendererDesc 

If you have Maya 2008-x64, copy 2008-x64/to_maya_bin_plug-ins/maxwell.so to $MAYA_HOME/bin/plug-ins and
2008-x64/to_maya_bin_plug-ins_image/IMFMXI.so $MAYA_HOME/bin/plug-ins/image

If you have Maya 8.5-x64, copy 8.5-x64/to_maya_bin_plug-ins/maxwell.so to $MAYA_HOME/bin/plug-ins and
8.5-x64/to_maya_bin_plug-ins_image/IMFMXI.so $MAYA_HOME/bin/plug-ins/image

If you have Maya 8.0-x64, copy 8.0-x64/to_maya_bin_plug-ins/maxwell.so to $MAYA_HOME/bin/plug-ins and
8.0-x64/to_maya_bin_plug-ins_image/IMFMXI.so $MAYA_HOME/bin/plug-ins/image

2.-Set up the environment:

Define the following environment variables in your shell:

MAXWELL_ROOT="maxwell installation path"
LD_LIBRARY_PATH="maxwell installation path":$LD_LIBRARY_PATH

For example, if maxwell is installed in /opt/local/maxwell64-1.6 and you use BASH, add the 
following lines in $HOME/.bash_profile:

export MAXWELL_ROOT=/opt/local/maxwell64-1.6
export LD_LIBRARY_PATH=/opt/local/maxwell64-1.6:$LD_LIBRARY_PATH

or if you use C-Shell, add the following in .cshrc

setenv MAXWELL_ROOT /opt/local/maxwell64-1.6
setenv LD_LIBRARY_PATH /opt/local/maxwell64-1.6:$LD_LIBRARY_PATH


:)

---

