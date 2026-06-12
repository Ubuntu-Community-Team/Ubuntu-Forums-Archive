---
title: "Ubuntu on a Novell Network"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by dodgi on 2005-07-27
I'm trying to set up an Ubuntu box on our college Novell network, so far without success. I have downloaded the linux novell client package from novell but haven't been able to successfully install it. Firstly it is an RPM package. I used Alien to convert this to a Debian package but am not sure that I have done everything I should have (this was the first time I have tried this).

Has anyone successfully connected a ubuntu box to a Novell network and if so how did you achieve this?

Cheers

Dodgi

---

### Post by dodgi on 2005-07-28
One bump cos I really need to crack this one and am getting nowhere :)

---

### Post by DW5 on 2005-07-28
I'm in the same boat. As a newbie, I decided to strike out give it a try.

 I downloaded the NCL_disk-NLD-bld622.tar.gz file from novell, extracted all the rpm files (there were only two .i386 files and a load of .i586 files)and installed them with alien (alien -i ....rpm)  Currently, Synaptic shows them all installed, but that's where I sit.  

I rebooted to see if the nautilus plugin would appear somewhere and give me a shot at trying to configure.  

I do a locate for files with novell or whathaveyou in them, and get no results.

Not knowing enough about the install procedures, I'm stuck.

This would be a great fix for ubuntu to help folks who have to exist novell server situations to make the total switch.  This is all that stands in my way of ubuntu happiness.

---

### Post by DW5 on 2005-07-28
I have tried running the novell install script, but it wants rpms.  I'm not enough of a programmer to know how to get it to unpack the mess I created by running alien -i on all those rpms it wants. I thought someone might be able to parse it though.

```
#! /bin/bash
#------------------------------------------------------------------------------
#
# ncl_install
#
#------------------------------------------------------------------------------
# Comments to:
#   support@novell.com
#------------------------------------------------------------------------------
# Copyright 2005, Novell, Inc.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Public License for more details.
#
# This script and its embedded programs are distributed with
# absolutely, positively NO WARRANTY WHATSOEVER, without even the
# implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR
# PURPOSE.  The author and Novell, Inc. take no responsibility for
# the consequences of running this script.
#------------------------------------------------------------------------------
#
#   START_DIR = pwd - the current working directory
#
#------------------------------------------------------------------------------

VERSION=1.10
SCRIPT_NAME='ncl_install'
START_DIR=`pwd`

if [ -z "$1" ]
then
    MODE="install"
else
    MODE=$1
    if [ -z "$2" ]
    then
        OPTION=""
    else
        OPTION=$2
    fi
fi

# fix this translate all the echo commands?
echo ""
echo "[$SCRIPT_NAME] $SCRIPT_NAME v$VERSION started"
echo "[$SCRIPT_NAME] mode = $MODE"
echo "[$SCRIPT_NAME] option = $OPTION"
echo ""

# verify that a valid mode was entered
case "$MODE" in
    "install" | "verify" | "uninstall" | "information" | "files" )
    #echo "[$SCRIPT_NAME] $MODE is valid"
    ;;

    "usage" | "help" | "?" )
    #echo "[$SCRIPT_NAME] $MODE is valid"
    echo ""
    echo "[$SCRIPT_NAME] usage:  $SCRIPT_NAME  [ install | uninstall | verify | information | files ] [ force ]"
    echo ""
    exit 1
    ;;

    * )
    echo ""
    if [ -n "$1" ]
    then
        echo "[$SCRIPT_NAME] invalid mode: <$MODE>"
    fi
    echo "[$SCRIPT_NAME] usage:  $SCRIPT_NAME  [ install | uninstall | verify | information | files ] [ force ]"
    echo ""
    exit 1
    ;;
esac
    
# verify that a valid option was entered
case "$OPTION" in
    "force" )
    #echo "[$SCRIPT_NAME] $OPTION is valid"
    if [ "$MODE" != "install" ]
    then
        echo ""
        echo "[$SCRIPT_NAME] invalid option <$OPTION> for mode: <$MODE>"
        echo "[$SCRIPT_NAME] usage:  $SCRIPT_NAME  [ install | uninstall | verify | information | files ] [ force ]"
        echo ""
        exit 1
    fi
    ;;

    * )
    if [ -n "$2" ]
    then
        echo ""
        echo "[$SCRIPT_NAME] invalid option: <$OPTION>"
        echo "[$SCRIPT_NAME] usage:  $SCRIPT_NAME  [ install | uninstall | verify | information | files ] [ force ]"
        echo ""
        exit 1
    fi
    ;;
esac
    
# validate that the user running the script is root
ROOT_UID=0
#echo "[$SCRIPT_NAME] User id = <$UID>"
#echo "[$SCRIPT_NAME] Root user id = <$ROOT_UID>"
if [ "$UID" -ne "$ROOT_UID" ]
then
    echo ""
    echo "[$SCRIPT_NAME] ERROR: You are not the root user."
    echo "[$SCRIPT_NAME] To install the Novell Client for Linux,"
    echo "[$SCRIPT_NAME] you must login as the root user."
    echo ""
    exit 2
fi

# verify that the script was launched from the right location
if [ "$MODE" = "install" ]
then
    if [ ! -e $START_DIR/novell ]
    then
        echo ""
        echo "[$SCRIPT_NAME] ERROR: script was launched from an invalid location:"
        echo "[$SCRIPT_NAME] $START_DIR"
        echo "[$SCRIPT_NAME] The 'novell' directory is missing."
        echo ""
        exit 3
    fi
fi

# set the necessary variables based on the mode
case "$MODE" in
    "install" )
    ACTION="Installing"
    ACTION_QUESTION="install"
    ACTION_PAST_TENSE="Installation"
    RPM_PARAM="-U"
    RPM_PATH="$START_DIR/novell/"
    ;;

    "uninstall" )
    ACTION="Uninstalling"
    ACTION_PAST_TENSE="Uninstallation"
    RPM_PARAM="-e"
    RPM_PATH=""
    ;;

    "verify" )
    ACTION="Verifying the installation of"
    ACTION_QUESTION="verify the installation of"
    ACTION_PAST_TENSE="Installation verification"
    RPM_PARAM="-V"
    RPM_PATH=""
    ;;

    "information" )
    ACTION="Querying information in"
    ACTION_QUESTION="query the information in"
    ACTION_PAST_TENSE="Information query"
    RPM_PARAM="-qi"
    RPM_PATH=""
    ;;

    "files" )
    ACTION="Querying file list in"
    ACTION_QUESTION="query the file list in"
    ACTION_PAST_TENSE="File list query"
    RPM_PARAM="-ql"
    RPM_PATH=""
    ;;

    * )
    echo "[$SCRIPT_NAME] ERROR: invalid mode: <$MODE>"
    echo ""
    exit 4
    ;;
esac

# set the necessary variables based on the option
case "$OPTION" in
    "force" )
    echo ""
    echo "[$SCRIPT_NAME] Are you sure you want to force"
    echo "[$SCRIPT_NAME] the installation of the Novell Client"
    echo "[$SCRIPT_NAME] by ignoring package and file conflicts?."
    echo -n "[$SCRIPT_NAME] (y/n) "
    read FORCE
    if [ $FORCE = "y" ]
    then    
        ACTION="Forcing the installation of"
        ACTION_QUESTION="force the installation of"
        ACTION_PAST_TENSE="Forced installation"
        RPM_PARAM="-U --force "
        RPM_PATH="$START_DIR/novell/"
    else
        echo ""
        exit 5
    fi
    ;;

    * )
    if [ -n "$2" ]
    then
        echo "[$SCRIPT_NAME] ERROR: invalid option: <$OPTION>"
        echo ""
        exit 6
    fi
    ;;
esac

# display the RPM options
echo "[$SCRIPT_NAME] This script uses the following RPM options:"
echo "[$SCRIPT_NAME] $RPM_PARAM"
echo "[$SCRIPT_NAME] For a description of these options,"
echo "[$SCRIPT_NAME] see the RPM documentation."

cd $START_DIR
echo ""
echo "[$SCRIPT_NAME] $ACTION the Novell Client for Linux."
echo "[$SCRIPT_NAME] Please wait..."
echo ""

# create the list of rpms
if [ $MODE = "uninstall" ]
then
    RPM_LIST="novell-client
    novell-client-yast2
    novell-qtgui
    novell-ui-base
    novell-xplatlib
    novell-novfsd
    novell-novfs
    novell-xtier-core
    novell-xtier-base
    novell-nmasclient
    nici"
elif [ $MODE = "install" ]
then
    RPM_LIST="nici
    novell-nmasclient
    novell-xtier-base
    novell-xtier-core
    novell-novfs
    novell-novfsd
    novell-xplatlib
    novell-ui-base
    novell-client-script
    novell-client-yast2
    novell-client"
else
    RPM_LIST="nici
    novell-nmasclient
    novell-xtier-base
    novell-xtier-core
    novell-novfs
    novell-novfsd
    novell-xplatlib
    novell-ui-base
    novell-qtgui
    novell-client-script
    novell-client-yast2
    novell-client"
fi

# uninstall the optional plugin rpms
if [ $MODE = "uninstall" ]
then
    RPM_PLUGIN_LIST="novell-konqueror-plugin
        novell-nautilus-plugin"
    for RPM_PLUGIN_NAME in $RPM_PLUGIN_LIST
    do 
        echo ""
        echo "[$SCRIPT_NAME] $ACTION (optional rpm) $RPM_PLUGIN_NAME..."
    
        # launch rpm
        rpm $RPM_PARAM $RPM_PLUGIN_NAME
    done
fi

# uninstall the novell-client-conf rpm
if [ $MODE = "uninstall" ]
then
    RPM_CONF_NAME="novell-client-conf"
    echo ""
    echo "[$SCRIPT_NAME] $ACTION (optional rpm) $RPM_CONF_NAME..."

    # launch rpm
    rpm $RPM_PARAM $RPM_CONF_NAME
fi 

# perform the requested action based on the mode
RPM_RESULTS="success"
for RPM_NAME in $RPM_LIST
do 
    echo ""
    echo "[$SCRIPT_NAME] $ACTION $RPM_NAME..."

    case "$RPM_NAME" in
        "nici" | "novell-nmasclient"  )
        RPM_ARCH="i386/"
        ;;
    
        "novell-xtier-base" | "novell-xtier-core" | "novell-novfs" | "novell-novfsd" | "novell-xplatlib" | "novell-client-script" | "novell-client-yast2" | "novell-ui-base" | "novell-qtgui" | "novell-konqueror-plugin" | "novell-nautilus-plugin" | "novell-client"  )
        RPM_ARCH="i586/"
        ;;
    
        * )
        RPM_ARCH="unknown/"
        ;;
    esac

    case "$MODE" in
        "install" )
        # get the full name of the rpm
        if [ $RPM_NAME = "novell-client" ];
        then
            # fix this - you need a better way to do this
            RPM_FULL_NAME=`ls $RPM_PATH$RPM_ARCH$RPM_NAME-0*`
        else
            RPM_FULL_NAME=`ls $RPM_PATH$RPM_ARCH$RPM_NAME-*`
        fi
        # add novell-qtgui to novell-client-script
        if [ $RPM_NAME = "novell-client-script" ];
        then
            ADDITIONAL_RPM_NAME="novell-qtgui"
            echo "[$SCRIPT_NAME] and $ADDITIONAL_RPM_NAME..."
            NCS_RPM_FULL_NAME=`ls $RPM_PATH$RPM_ARCH$ADDITIONAL_RPM_NAME-*`
            RPM_FULL_NAME="$RPM_FULL_NAME $NCS_RPM_FULL_NAME"
        fi
        # launch rpm
        rpm $RPM_PARAM $RPM_FULL_NAME
        ;;
    
        "uninstall" )
        # add novell-client-script to novell-qtgui
        if [ $RPM_NAME = "novell-qtgui" ];
        then
            ADDITIONAL_RPM_NAME="novell-client-script"
            echo "[$SCRIPT_NAME] and $ADDITIONAL_RPM_NAME..."
            RPM_NAME="$RPM_NAME $ADDITIONAL_RPM_NAME"
        fi
        # launch rpm
        rpm $RPM_PARAM $RPM_NAME
        ;;
    
        "verify" | "information" | "files" )
        # launch rpm
        rpm $RPM_PARAM $RPM_NAME
        ;;
    
        * )
        echo "[$SCRIPT_NAME] ERROR: invalid mode: <$MODE>"
        echo ""
        exit 6
        ;;
    esac
    
    if [ $? != 0 ];
    then
        echo "[$SCRIPT_NAME] ERROR: $ACTION_PAST_TENSE of the $RPM_NAME rpm failed."
        RPM_RESULTS="failure"
    fi
done

# perform all other actions on the novell-client-conf rpm
RPM_CONF_NAME="novell-client-conf"
RPM_ADDON_PATH="$START_DIR/add-on/novell-client-conf/"
case "$MODE" in
    "install" )
    if [ -e $RPM_ADDON_PATH/$RPM_CONF_NAME-*.rpm ]
    then
        echo ""
        echo "[$SCRIPT_NAME] $ACTION (optional rpm) $RPM_CONF_NAME..."
        RPM_FULL_NAME=`ls $RPM_ADDON_PATH$RPM_CONF_NAME-*`
        rpm $RPM_PARAM $RPM_FULL_NAME
        if [ $? != 0 ];
        then
            echo "[$SCRIPT_NAME] $ACTION_PAST_TENSE of the $RPM_CONF_NAME rpm failed."
        fi
    fi
    ;;

    "verify" | "information" | "files" )
    echo ""
    echo "[$SCRIPT_NAME] $ACTION (optional rpm) $RPM_CONF_NAME..."
    rpm $RPM_PARAM $RPM_CONF_NAME
    ;;
esac
        
# process the optional plugin rpms
if [ $MODE != "uninstall" ]
then
    RPM_PLUGIN_LIST="novell-konqueror-plugin
        novell-nautilus-plugin"
    for RPM_PLUGIN_NAME in $RPM_PLUGIN_LIST
    do 
        CONTINUE="y"

        echo ""
        echo "[$SCRIPT_NAME] Do you want to $ACTION_QUESTION"
        echo "[$SCRIPT_NAME] the optional $RPM_PLUGIN_NAME rpm?"
        echo -n "[$SCRIPT_NAME] (y/n) "
        read CONTINUE
    
        if [ $CONTINUE = "y" ]
        then
            echo ""
            echo "[$SCRIPT_NAME] $ACTION (optional rpm) $RPM_PLUGIN_NAME..."
        
            RPM_ARCH="i586/"
        
            case "$MODE" in
                "install" )
                # get the full name of the rpm
                RPM_FULL_NAME=`ls $RPM_PATH$RPM_ARCH$RPM_PLUGIN_NAME-*`
                # launch rpm
                rpm $RPM_PARAM $RPM_FULL_NAME
                if [ $? != 0 ];
                then
                    echo "[$SCRIPT_NAME] ERROR: $ACTION_PAST_TENSE of the $RPM_PLUGIN_NAME rpm failed."
                    RPM_RESULTS="failure"
                fi
                ;;
            
                "verify" | "information" | "files" )
                # launch rpm
                rpm $RPM_PARAM $RPM_PLUGIN_NAME
                if [ $? != 0 ];
                then
                    echo "[$SCRIPT_NAME] ERROR: $ACTION_PAST_TENSE of the $RPM_PLUGIN_NAME rpm failed."
                    RPM_RESULTS="failure"
                fi
                ;;
            
            esac
        fi
    done
fi

if [ $RPM_RESULTS = "success" ]
then
    echo ""
    echo "[$SCRIPT_NAME] $ACTION_PAST_TENSE of the Novell Client for Linux completed successfully."
else
    if [ $MODE = "verify" ]
    then
        echo ""
        echo "[$SCRIPT_NAME] Verification error definitions:"
        echo "[$SCRIPT_NAME] S....... size"
        echo "[$SCRIPT_NAME] .M...... mode"
        echo "[$SCRIPT_NAME] ..5..... MD5 checksum"
        echo "[$SCRIPT_NAME] ...D.... major and minor numbers"
        echo "[$SCRIPT_NAME] ....L... symbolic link contents"
        echo "[$SCRIPT_NAME] .....U.. owner"
        echo "[$SCRIPT_NAME] ......G. group"
        echo "[$SCRIPT_NAME] .......T modification time"
        echo "[$SCRIPT_NAME] ........ c indicates a configuration file"
    fi
fi
echo ""
exit
```

---

### Post by dodgi on 2005-07-29
Thnx for your contribution DW5. I went through the same steps as you and arrived at the same point. I also tried installing the linux client from

[http://novelclient.sourceforge.net/howto.html](http://novelclient.sourceforge.net/howto.html)

again without success. Following this install I get an 'error while loading shared libraries' when trying to run the Novel binary.

---

### Post by DW5 on 2005-08-01
After querying our IT people, it seems that our novell servers also allow SMB connections.  Thus, I have been able to connect to my novell network directories using SAMBA.  I think, though don't know, that this might be preferred since SAMBA is already running properly on my system, saves the overhead necessary to keep the novell client running, etc.

The directions given by our IT folks were:

Be sure login to the novell network from a windows machine using novell client 4.9 or later.  This creates a universal password on the novell system for accessing using other protocols.  Then login using SMB protocol.

So, I booted windows, logged in to the network, upgraded my Novell client to 4.91, rebooted, logged in again, rebooted back into Linux, then I:

went to Places | Connect to Server | selected Service Type: Custom and

inserted in the location  

smb://<username>@<hostname>

replacing username and host name appropriately.   This mounted the file server that contained my network directory.  I opened nautilus, saw the server, clicked on it.  It prompted me for my novell password, which I entered, then prompted me for my keyring password (I entered the password that I use to login to my ubuntu machine), it opened the server and I then drilled down to find my network home directory.  I copied the full URL for that home directory out of the location box and repeated the steps above to create a direct connection to the subdirectories I want.  It works great, even better I think than the novell client.  I later rebooted and it preserved the connection (just had to login again).

I don't know if all novell servers run able to connect with SMB, but it was sure easy to do. 

The IT folks also said our servers would connect using NFS, but that they hadn't configured it to do so, but would if I couldn't get SMB to work.  

If Novell servers will typically connect using SMB, this may really be the better approach than dowloading the novell client and trying to install it.  The only problem I suppose is what to do when the novell password expires.

Hope you can use this workaround.

DW

---

### Post by aarmelvin on 2008-01-15
@DW5

Thanks for ur valuable information.
Using Samba, i was able see my area i.e., /novell/STAFF/

then it asked for passward, i entered but it not allowing me to enter into the server.....

as u said first i gave username and passwd, then i gave my ubuntu systems username and passwd.......but its not working..........

plz help me

=====================================================================
actally from my network places, i entered like this

smb://aarmevin@novell/

then it shows all the folders......then i was trying to enter into STAFF folder, it asked for passwd...
i gave it, but its not working....................plz help me...
If its work.....i was planning to install Ubuntu in whole of our staff room systems..
thanks in advance...

i am waiting for ur reply

---

### Post by jrusso2 on 2008-01-15
I remember seeing the novell client in .deb package in the Xandros repository if its possible to download it and try it from there.

---

