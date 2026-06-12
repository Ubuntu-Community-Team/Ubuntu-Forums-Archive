---
title: "maxwell render for maya feisty"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by antonyant11 on 2008-03-30
Hi I am having trouble with these installation instructions. I can copy the files ok but am having trouble with 2.-Set up the environment:

-------------------------------------------------------------------------------------------------------------------

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

--------------------------------------------------------------------------------------------------------------------

everything is ok untill step two.  I have located .bash_profile I assume it is called .profile in feisty fawn. and have added the lines as follows

-------------------------------------------------------------------------------------------------------------

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"

fi
export MAXWELL_ROOT=/opt/local/maxwell64-1.6
export LD_LIBRARY_PATH=/opt/local/maxwell64-1.6:$LD_LIBRARY_PATH

--------------------------------------------------------------------------------------------------------------------

I restart open maya check the availabe renders and maxwell is not an option.

If anybody could help it would be much appreciated

---

