---
title: "root permissions"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by japc126 on 2006-11-17
How can I make my account have root permissions?

---

### Post by taurus on 2006-11-17
You need to belong to groups adm & admin in /etc/group!  To see if you belong to those two groups, open a terminal (Applications -> Accessories -> Terminal) and type

```
id
```

---

### Post by japc126 on 2006-11-17
I get this

uid=1000(jose) gid=1000(jose) groups=0(root),4(adm),20(dialout),21(fax),24(cdrom),
25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),
109(lpadmin),111(scanner),114(admin),115(fuse),1000(jose)

What does it means?

---

### Post by taurus on 2006-11-17
Open a terminal and see what happens when you run these two commands...

```
sudo aptitude update
sudo aptitude upgrade
(use the same password that you use to log in...)
```

---

### Post by japc126 on 2006-11-17
a lot of text rolled by, but I still don't have root permissions. Any more ideas?

---

### Post by steve.horsley on 2006-11-17
You can't make your account have root permissions - only root has root permissions. Neither should you log in as root (and in Ubuntu, you can't because the root account is disabled.

You can (from your account) arrange to run a process with root's priviledge by using the command sudo (a bit like playing Simon Says). See this link:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

What are you trying to do as root?

---

### Post by sindrum_murdnis on 2006-11-17
retract the last statement

---

### Post by taurus on 2006-11-17
> **japc126 said:**
> a lot of text rolled by, but I still don't have root permissions. Any more ideas?
Yes, you are running those two commands as root, sudo!  You don't actually need to log in as root to install stuff on your computer.  You can use sudo...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by japc126 on 2006-11-17
thanks

---

### Post by brander on 2006-11-18
Hi, as a relative newbie to Ubuntu, I have a problem with a second mounted EXT3 harddrive. I mounted it as SU from terminal and it works fine then but it is read-only when I access it as the normal user. Should I mount it as SUDO instead, or how can I change its permissions to read/write for me?

Thanks.

---

### Post by taurus on 2006-11-18
> **brander said:**
> Hi, as a relative newbie to Ubuntu, I have a problem with a second mounted EXT3 harddrive. I mounted it as SU from terminal and it works fine then but it is read-only when I access it as the normal user. Should I mount it as SUDO instead, or how can I change its permissions to read/write for me?

Thanks.
I already answered your question in another thread and it's probably best if you start a new one if you have a question/problem instead of piggyback on an old one.

---

### Post by brander on 2006-11-18
OK, sorry but I felt that my prob was relative to this post. Will change in future, forgive newbie.

---

### Post by taurus on 2006-11-18
> **brander said:**
> OK, sorry but I felt that my prob was relative to this post. Will change in future, forgive newbie.
Don't worry about it.  See if my direction solved your problem with permissions in the other thread!

---

### Post by ccerinojr on 2006-11-18
Hey guys. I am having a similar problem, kind of. I am trying to install the linux drivers for my cisco card. I attempted to install with the script they give you:

```
ccerinojr@uberlaptop:~/Desktop/linux$ sudo ./install
This script needs to be executed as root to operate properly
```

I am currently running the latest version of kubuntu. I was originally running ubuntu before and it let me do this just fine as up above. I am a bit perplexed as to why this is being so difficult. Any ideas would be appreciated.

---

### Post by taurus on 2006-11-18
> **ccerinojr said:**
> Hey guys. I am having a similar problem, kind of. I am trying to install the linux drivers for my cisco card. I attempted to install with the script they give you:

```
ccerinojr@uberlaptop:~/Desktop/linux$ sudo ./install
This script needs to be executed as root to operate properly
```

I am currently running the latest version of kubuntu. I was originally running ubuntu before and it let me do this just fine as up above. I am a bit perplexed as to why this is being so difficult. Any ideas would be appreciated.
Can you paste the output of these two commands from a terminal?

```
id
ls -la ~/Desktop/linux
```

---

### Post by ccerinojr on 2006-11-18
There was only one command I am trying to execute as root and that is the "sudo ./install" command. The line below that was the output it spat back out at me after executing that command.

---

### Post by steve.horsley on 2006-11-18
I have a feeling that sometimes scipts run under sudo don't take on root's persona as fully as they should, though I can't explain why. So try this instead:
[B]sudo su
./install[/B]

---

### Post by ccerinojr on 2006-11-18
Gave that whirl and no luck. Still tell me I need to run the script as root.

---

### Post by aysiu on 2006-11-18
> **ccerinojr said:**
> Gave that whirl and no luck. Still tell me I need to run the script as root.
Maybe something's wrong with the script. Can you post the output of this command? ```
cat install
```

---

### Post by junglepeanut on 2006-11-19
I just thought I would ask this question, I apologize if it is slightly off but it may help to explain the issue.

Are you the owner of the computer, i.e. you installed ubuntu onto the computer, or are you using someone else's. 

If you are the owner are you in another users account that you created and would like to make this user have root privileges. 

I ask these as normally if you are not allowed to use sudo on my computers, it does not say anything just acts like the command worked, but you are still not root.

---

### Post by ccerinojr on 2006-11-19
Yes I am the own of the computer. I do have permission to used sudo. I also gave  sudo su a try and it gave me direct root access. I even tried using the id command to make sure I was root and it gave me a uid = 0. 

Everything with the script looks alright. This issue confuses me so much because I used this script on numerous other distros including ubuntu. Kunbuntu should be no different. Oh well here is the script code.

```

#!/bin/sh
###############################################################
# kpciinstall 2.0.1 raw  4/17/02                              #
# kpciinstall 2.0.2 raw  4/17/02 Changes for RH 6.2           #
# kpciinstall 2.0.3 raw  4/17/02 Changes for user auth in wep #
# setkey functions.
# kpciinstall 2.0.4 taw  4/18/02 Fix compiler breakage        #
# Script to build/install the 2.0 version PCMCIA MIC and      #
# the miniPCI drivers and utilities. With -R argument         #
# utilities and drivers are removed                           #
# install 2.0.5          4/05/03 change the world             #
###############################################################

KERNEL_RELEASE=`uname -r`
SRCDIR=/usr/src/linux-`uname -r`
MODBASE="/lib/modules/`uname -r`"
SRCDIRS=`echo /usr/src/*`
ARCHDIR=`pwd`

KPCMCIA=""
LINUX24=`uname -r|grep 2\.4`>/dev/null
CSS=""
ALWAYSCOMPILE="n"
ALLINSTALL="n"
ALLREMOVE="n"
DRVREM="n"
UTLREM="n"
DRVINS="n"
UTLINS="n"
CURWD=""
CC=""           # Broken compiler fix for redhat 7.0

########################################################
# Command lines for compiling the drivers              #
########################################################
MPICMP='${CC} -MD  -O2 -Wall -Wstrict-prototypes -pipe -I${SRCDIR}/include -D__KERNEL__ -DMODULE -c mpi350.c'
AIROCMP='${CC} -MD -O2 -Wall -Wstrict-prototypes -pipe -I${SRCDIR}/include -D__KERNEL__ -DMODULE -c airo.c'
AIROCSCMP='${CC} -MD -O2 -Wall -Wstrict-prototypes -pipe -I${SRCDIR}/include -D__KERNEL__ -DMODULE -c airo_cs.c'
CBCMP='${CC} -MD  -O2 -Wall -Wstrict-prototypes -pipe -I${SRCDIR}/include -D__KERNEL__ -DMODULE -c cb20_cb.c'


#############################################################
# Usage: install -options
# Note: dash (-) necessary
# -C always compile drivers 
# -R remove all 
# -rd remove drivers
# -ru remove utilities
# -iu install utilities
# -id install drivers
# No arguments installs everything overwriting previous 
# install if it exists.
#############################################################

if [ "$UID" != "0" ]
then
  echo "This script needs to be executed as root to operate properly."
  exit 1
fi

if [ $# -ne 0 ]
then     
  while getopts ":i:du:r:du:RC" Option
  do
     case $Option in
      C ) ALWAYSCOMPILE="y";;
      R ) ALLREMOVE="y";;
      r ) 
	case $OPTARG in 
		d) echo "Remove drivers";DRVREM="y" ;; 
		u) echo "Remove utils";UTLREM="y" ;;
		*) echo "Unrecognized remove command \"$OPTARG\" exiting.";exit 1;;
	esac
	;;
      i ) echo  "Install #4: option -i-, with argument \"$OPTARG\""
	case $OPTARG in 
		d) echo "Install drivers";DRVINS="y";;
		u) echo "Install utils";UTLINS="y";;
		*) echo "Unrecognized install command \"$OPTARG\" exiting.";exit 1;;
	esac
	;;
      * ) echo "Unrecognized Option $OPTARG  exiting";exit 1;;   
     esac
  done
  shift $(($OPTIND - 1))  
else
   ALLINSTALL="y"
fi
if [[ ${DRVINS} = "n" && ${DRVREM} = "n" && ${UTLINS} = "n" && ${UTLREM} = "n" && ${ALLREMOVE} = "n" ]]
then
    ALLINSTALL="y"
fi

if [[ ${ALLINSTALL} = "y" || ${UTLINS} = "y" || ${DRVINS} = "y" ]]
then
    more EULA.txt
    echo
    echo "Do you accept this license (y/n)?"
    read ans
    if [[ ${ans} != "y" && ${ans} != "Y" ]]
    then
        exit 1
    fi
fi

bad="n"
if [[ ${ALLINSTALL} = "y" || ${UTLINS} = "y" ]]
then
    ldcmd="ldconfig"
    cmdout=`type -p $ldcmd`
    if [ -z $cmdout ]
    then
        ldcmd="/sbin/ldconfig"
        cmdout=`type -p $ldcmd`
        if [ -z $cmdout ]
        then
            ldcmd="/usr/sbin/ldconfig"
            cmdout=`test -p $ldcmd`
            if [ -z $cmdout ]
            then
                echo "Cannot find ldconfig. Cannot test for necessary libraries."
                ldcmd=""
            fi
        fi
    fi
echo ldcmd $ldcmd
    if [ -n "$ldcmd" ]
    then
        echo "Checking for libsigc++ ..."
        lib=`$ldcmd -N -X --print-cache | grep "libsigc-1.0.so.0"`
        if [ -z "$lib" ]
        then
            echo "libsigc++ not installed."
            bad="y"
        else
            echo "libsigc++ found."
        fi
        echo "Checking for gtkmm ..."
        lib=`$ldcmd -N -X --print-cache | grep "libgtkmm-1.2.so.0"`
        if [ -z "$lib" ]
        then
            echo "libgtkmm not installed."
            bad="y"
        else
            echo "libgtkmm found."
        fi
    fi
fi

if [ $bad = "y" ]
then
    echo
    echo "The libraries can be downloaded from the web."
    echo
    echo "Sources are available from sourceforge.net (projects gtkmm and"
    echo "libsigc++). Be sure that you download the correct versions (1.2.10"
    echo "of gtkmm and 1.0.4 of libsigc++). You must install libsigc++ before"
    echo "you can install gtkmm."
    echo
    echo "RPM packages of the libraries can be obtained from freshrpms.net."
    exit 1
fi

echo
echo "Continuing ..."

####################################################
# Broken compiler FIX  avoid using broken compiler #
# to build drivers                                 #
####################################################
fixrh70() {
    if [ -x /usr/bin/kgcc ]
    then
	CC=kgcc
    else
	CC=cc
    fi
}

##################################################
# Find any ethernet adapters, originally written #
# by Jim Venesky adapted by Roland Wilcher       #
##################################################

find_ethernets(){
    echo "Now attempting to determine how many Ethernet cards you have installed."
    # first check and see if we already have an Aironet card installed with
    # another (Ben Reeds) driver
    mytest=`ifconfig 2> /dev/NULL`
    if [ -z "$mytest" ]
    then
      cmd="/sbin/ifconfig"
    else
      cmd="ifconfig"
    fi
    adapter=`${cmd} -a | egrep "00:40:96|00:07:50|00:01:64" | tail --lines=1 | cut -c 4`
    if [ -z "$adapter" ]
    then
	# no Aironet cards detected - look for other Ethernet cards...
        adapter=`${cmd} -a | grep eth | tail --lines=1 | cut -c 4`
    if [ "1$adapter" -eq "1" ]
    then
	adapter="-1"
        echo "You currently have no Ethernet adapters installed."
    else
	echo "You already have a non-Aironet Ethernet adapter."
    fi
	next_adapter=`expr $adapter + 1`
    else
        echo "You already have an Aironet card installed as eth$adapter."
	next_adapter=$adapter
    fi
    
    # copy over a new version of the default config file
    # otherwise acu may get upset if it finds an old style one

    if [ -f ${ARCHDIR}/ethX.cfg ]
    then
        cp ${ARCHDIR}/ethX.cfg /etc/eth$next_adapter.cfg
	chmod a+rw /etc/eth$next_adapter.cfg
    else
	echo "ERROR - ethX.cfg was not found."
        echo "Please run the install from the directory containing the contents o
f the driver/utility archive."
        exit 1
    fi
}



########################################
# Find kernel sources                  #
########################################
find_source(){
    for i in ${SRCDIRS} 
    do
	if [ -d $i ]
	then 
	    LDIR=$i
	    if [ -d ${i}/Documentation ]
	    then
		SRCDIR=${LDIR}
		break 
	    fi
	else
	    SRCDIR=""
	fi
    done
}

# Function to test for kernel PCMCIA

check_kernel_pcc()
{
    KCSS=`/sbin/lsmod|grep ^yenta|cut -d' ' -f1` >/dev/null
    if [ ${KCSS}X = X  ]
    then 
       KPCMCIA="N"
    else
       KPCMCIA="Y"
    fi
}

# function to test for card and socket
# services.

check_cs_pcc()
{
    KCSS=`/sbin/lsmod|grep ^i82365|cut -d' ' -f1` >/dev/null

    if [ ${KCSS}X = X  ]
    then 
       CSS="N"
    else
       CSS="Y"
    fi
}

#############################################
# Ask for the source directory, Just hitting# 
# return will abort the install             #
#############################################

ask4src(){
    echo -n "Please enter the path to your kernel sources: "
    read SRCDIR
    if [ ${SRCDIR}H = "H" ]
    then
      echo "Module compilation aborted."
      exit 1;
    fi
}

# Remove everything

remove(){

    echo "Removing Cisco/Aironet drivers and utilities"
    rm -rf /opt/cisco         # Remove utilities
    rm -f /etc/eth?.cfg       # remove config files.

    if [ ${LINUX24}X != X ]
    then
	rm -f ${MODBASE}/kernel/drivers/net/mpi350.o
	rm -f ${MODBASE}/kernel/drivers/net/pcmcia/airo.o
	rm -f ${MODBASE}/kernel/drivers/net/airo.o
    else
	rm -f ${MODBASE}/net/mpi350.o
	rm -f ${MODBASE}/net/mpi350.o
	rm -f ${MODBASE}/pcmcia/airo.o
	rm -f ${MODBASE}/net/airo.o
	echo "Cisco/Aironet utilities and drivers have been removed"
    fi
	exit 0

}
 
remove_utils(){
    echo "Removing Cisco/Aironet utilities only"
    rm -rf /opt/cisco
    rm -f /etc/eth?.cfg
    echo "Cisco/Aironet utilities have been removed"
    exit 0;
}


remove_drivers(){

    if [ ${LINUX24}X != X ]
    then
	rm -f ${MODBASE}/kernel/drivers/net/mpi350.o
	rm -f ${MODBASE}/kernel/drivers/net/pcmcia/airo.o
	rm -f ${MODBASE}/kernel/drivers/net/airo.o
    else
	rm -f ${MODBASE}/net/mpi350.o
	rm -f ${MODBASE}/pcmcia/airo.o
	rm -f ${MODBASE}/net/airo.o
    fi	

    echo "Cisco/Aironet drivers have been removed"
    exit 0
}
   
remove_all(){
    echo "Removing Cico/Aironet drivers and utilities"

    rm -rf /opt/cisco         # Remove utilities
    rm -f /etc/eth?.cfg       # remove config files.
    rm -f ${MODBASE}/kernel/drivers/net/mpi350.o
    rm -f ${MODBASE}/kernel/drivers/net/pcmcia/airo.o
    rm -f ${MODBASE}/kernel/drivers/net/airo.o
    
    echo "Cisco/Aironet utilities and drivers have been removed"
    exit 0
}

#################################################
# Install device drivers                
#################################################

install_drivers(){
    cd ${CURWD}
    if [ ! -d driver ]
    then
	echo "Please run the install from the directory containing the "
	echo "contents of the driver and utility archive."
	exit 1
    fi
    
    fixrh70  # fix cc breakage for RH7.0

    GOOD="n"
    if [ ${GOOD} = "n" ]
    then
        cd driver

        find_source

        if [ ${SRCDIR}X = X ]
        then
            while [ ! -d ${SRCDIR}/Documentation ]
            do
                echo "Cannot locate source in ${SRCDIR} "
                ask4src
            done
        fi

        echo "Please wait , Compiling driver modules using sources in ${SRCDIR}"

        fixrh70
        eval ${MPICMP}
        eval ${AIROCMP}
        eval ${AIROCSCMP}
#        eval ${CBCMP}
        copy_drivers

    fi
}

copy_drivers(){
    find_ethernets;

    if [ ${KPCMCIA} = "Y" ]
    then
        echo "Your system is configured with kernel PCMCIA services"
        cp airo.o ${MODBASE}/kernel/drivers/net/pcmcia/airo.o
        cp airo_cs.o ${MODBASE}/kernel/drivers/net/pcmcia/airo_cs.o
#       cp cb20_cb.o ${MODBASE}/kernel/drivers/net/cb20_cb.o
    fi

    if [ ${CSS} = "Y" ]
    then
        cp airo.o ${MODBASE}/pcmcia/
    fi
    #############################
    # PCI only install          #
    #############################
    if [ ${CSS} = "N" ]
    then
        if [ ${KPCMCIA} = "N" ]
        then
            if [  ${LINUX24}X != X ]
            then
                cp airo.o ${MODBASE}/kernel/drivers/net
            else
                cp airo.o ${MODBASE}/net
            fi
        fi
    fi

    if [  ${LINUX24}X != X ]
    then
        cp mpi350.o ${MODBASE}/kernel/drivers/net
    else
        cp mpi350.o ${MODBASE}/net
    fi

    cd ..

    /sbin/depmod
}

##############################################################################
# Install itilities                                                          #
# check and see if this directory exists - if it does see if it is writable  #
# if it does not exist - attempt to create it.                               #
# if we fail - exit out with an error message.                               #
##############################################################################

install_utils(){

location="/opt/cisco/bin"

cd ${CURWD}

if [ -d $location ]
then 
    if [ -w $location ]
    then
	echo ""
    else
	echo "ERROR - the utilities can not be installed in /opt/cisco/bin"
	echo "Exiting installation"
	exit 1
    fi
    else
	mkdir -p $location 2> /dev/null
	if [ -d $location ]
	then
	    echo "/opt/cisco/bin successfully created"
	else
	    echo "ERROR - unable to create /opt/cisco/bin"
	    echo "try to create it by hand and re-run install."
	    exit 1
	fi
   fi

   ############################################################
   # attempt to copy the utilities and help files from the    #
   # unpacked archive to /opt/cisco/{bin/helpml} utilities to #
   # install:  acu,bcard,leapset, leapscript,leaplogin        #
   ############################################################

    echo -n "Installing the utilities: "

#    if [ -z `uname -r | grep 2.4.18` ] 
#    then
#        release="redhat90"
#    else
#        release="redhat73"
#    fi
    if [ -z "`ldd -d -r utilities/redhat73/acu 2>&1 | grep undefined`" ]
    then
        release="redhat73"
    else
        if [ -z "`ldd -d -r utilities/redhat90/acu 2>&1 | grep undefined`" ]
        then
            release="redhat90"
        else
            echo ""
            echo "There is one or more problems with running the ACU."
            echo "If you have not installed the correct versions of the"
            echo "libraries, please install them and re-run this script."
            echo ""
            echo "If this is not the case, you might be using an unsupported configuration."
            echo "RedHat 7.3, RedHat 9.0 and Suse 9.0 are supported."
            echo ""
            exit 1
        fi
    fi
    for utility in acu bcard leapset leapscript leaplogin
    do
	if [ -f "utilities/$release/$utility" ]
	then
	    cp utilities/$release/$utility $location
	    chmod a+x $location/$utility
	    echo -n "$utility "
	else
	    echo ""
	    echo "ERROR - $utility was not found."
	    echo "Please run the install from the directory containing the contents of the driver/utility    archive."
	    exit 1
	fi
    done

    if [ -f ACU.PRFS ]
    then
	cp ACU.PRFS /opt/cisco
	chmod a+rw /opt/cisco/ACU.PRFS
    fi

    echo ""
    if [ -f "helpml.tar.gz" ]
    then
	echo "Installing Help Files..."
	cp helpml.tar.gz /opt/cisco
	pushd /opt/cisco > /dev/null
	tar zxf helpml.tar.gz
	rm -f helpml.tar.gz
	popd > /dev/null
	echo "Help Files installed."
    else
	echo "ERROR - the help file archive was not found: helpml.tar.gz"
	echo "Please run the install from the directory containing the contents of the driver/utility archive."
	exit 1
    fi
 echo ""
}

# Begin

CURWD=`pwd`
check_kernel_pcc
check_cs_pcc

#################################################
# Giving an -R argument to this script will     #
# remove all  utilities and drivers.            #
#################################################


if [ ${ALLREMOVE} = "y" ]
then 
    clear 
    echo -n "Remove drivers and utilities from the system are you sure (y/n):"
    read ANS
    
    if [ $ANS = "y" ]
    then 
	remove
    elif [ $ANS = "Y" ]
    then 
	remove
    else
	echo "Not verified no action taken."
    fi
    exit 0
fi

#################################################
# -rd removes the drivers from the system       #
#################################################
if [ ${DRVREM} = "y" ]
then
   clear
   echo -n "Remove Aironet drivers from the system are you sure (y/n):"
   read ANS

    if [ $ANS = "y" ]
    then 
	remove_drivers
    elif [ $ANS = "Y" ]
    then 
	remove_drivers
    else    
	echo "Not verified no action taken."
    fi
    exit 0
fi

####################################################
# -ru removes the utilities from system.           #
####################################################
if [ ${UTLREM} = "y" ]
then
   clear
   echo -n "Remove Aironet utilities are you sure (y/n):"
   read ANS

   if [ $ANS = "y" ]
   then 
       remove_utils
   elif [ $ANS = "Y" ]
   then 
       remove_utils
   else
	echo "Not verified no action taken."
   fi
   exit 0
fi

####################################################
# -id install drivers                              #
####################################################
if [ ${DRVINS} = "y" ]
then
    echo
    echo "Installing Cisco/Aironet drivers"

    install_drivers;
    echo "Drivers installed"
    exit 0
fi

####################################################
# -iu install utils                                #
####################################################
if [ ${UTLINS} = "y" ]
then
    echo
    install_utils
    echo "Utilities installed"
    exit 0
fi

####################################################
# no args install everything                       #
####################################################

if [ ${ALLINSTALL} = "y" ]
then
  echo
  install_drivers
  install_utils
  echo "Drivers and utilities installed"
  exit 0
fi


```

---

### Post by taurus on 2006-11-19
Change the first line to look like

```
#!/bin/bash
```

---

### Post by ccerinojr on 2006-11-19
Sorry guys I gave up because of frustration. I moved back to Ubuntu and I the script ran fine and my drivers are installed.

---

### Post by steve.horsley on 2006-11-19
Chaning the first line from #!/bin/sh to #!/bin/bash would definitely fix it. That dash thing they put info Edgy is badly busted. Even just
**echo $UID**
doesn't work.

---

### Post by Gaweph on 2006-11-19
> **japc126 said:**
> How can I make my account have root permissions?

You should try not to log into an account that has root for any period of time if you can help it.

Anyone who is able to get into (crack) your machine will have the same proivoilages as the user that is using the machine (its one of the reasons why linux is so secure)

Even if someone gets in, they only have limited privil;ages, and so cant realyly do much.  Imagine if you were logged in as root, when they got in, they could do anything they wanted to.

Just my $0.02

---

