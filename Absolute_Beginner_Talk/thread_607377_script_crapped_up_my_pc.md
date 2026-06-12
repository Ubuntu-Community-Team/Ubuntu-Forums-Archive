---
title: "script crapped up my pc"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-11-08
well, I used the bp-compiz script and it installed a ton of KDE crap, I didn't want it (and I decided the script wasn't for me.) I told it to uninstall the components it had installed... But they were still there...:(

here are screenys of all of it:

no screeny for konquerer but it's there as well (don't like konquerer.)

all the ones checked are the ones that were installed... rrrrrrr

---

### Post by nikoPSK on 2007-11-08
wwaaaaa, please help me clean it up...:(

---

### Post by llamakc on 2007-11-08
Have patience. Post the script wrapped in the code tags.

---

### Post by nikoPSK on 2007-11-08
```
#!/bin/bash
##############################################################################
# Bulletproof CF Automated Compilation Script                                #
# Author: phaed                                                              #
# Based on an excellent script by ElmonGW                                    #
##############################################################################
# Licensed under a Creative Commons Attribution-Noncommercial 3.0 License.   #
# http://creativecommons.org/licenses/by-nc/3.0/                             #
##############################################################################

downdir=~/.compiz-setup            # directory where were going to store source files
desktop=                           # kde or gnome (must be lowercase) or leave blank to get prompted
opdesktop=                         # leave blank
nvidia=`sed -n '/Section \"Device\"/,/EndSection/s/^ *Driver *"\([^"]*\)" */\1/p' /etc/X11/xorg.conf`


function echo_bold {
    echo $2 -e "\\033[1m$1\\033[0m"
}

function success {
    echo -e "\\033[1;32m[OK]\\033[0m"
}

function failure {
    record[$1]="\\033[1;31m[Error $2]\\033[0m"
    echo -e "\\033[1;31m[Failed]\\033[0m The previous process exited with error \\033[1m$2\\033[0m"
    [ "0$install_menu_choice" -eq 0 ] && exit 1
}

function header {
    clear
    echo -e "\033[7m    Bulletproof CF Script    \033[0m   <Press [Enter] for \\033[1mDefault\\033[0m>     Quit: [Ctrl-C]"
    echo
}

function footer {
    echo 
    echo "$1"
    echo
}

function footer_n {
    echo 
    echo -n "$1"
}

function _pause {
    echo 
    echo_bold "Press [Enter] to go back to the previous menu." "-n"
    read NULL
}

function remove_old {
    echo_bold "Removing any old versions..."
    sudo apt-get --assume-yes --force-yes remove emerald
    sudo apt-get --assume-yes --force-yes remove emerald-*
    sudo apt-get --assume-yes --force-yes remove emerald*
    sudo apt-get --assume-yes --force-yes remove compiz
    sudo apt-get --assume-yes --force-yes remove compiz-*
    sudo apt-get --assume-yes --force-yes remove compiz*
    sudo apt-get --assume-yes --force-yes remove beryl
    sudo apt-get --assume-yes --force-yes remove beryl-*
    sudo apt-get --assume-yes --force-yes remove beryl*
    sudo apt-get --assume-yes --force-yes remove desktop-effects
} 

function req_deps {
    echo_bold "Installing required dependencies to build..."
    (sudo apt-get --assume-yes --force-yes install git-core automake build-essential intltool libtool python python-pyrex python-gtk2 python2.5-dev python-qt4 python-qt4-dev && success) || failure 2  $?
}

function compiz_deps {    
    echo_bold "Insalling Compiz Fusion 's dependencies..."

    if [ "$deps_choice" = "0" ];then
        (sudo apt-get --assume-yes --force-yes build-dep compiz && success 3) || failure 3 $?
    elif [ "$desktop_choice" = "0" ]; then
        (sudo apt-get --assume-yes --force-yes install autoconf automake1.7 autotools-dev build-essential debhelper dpkg-dev g++ g++-4.1 html2text intltool libart-2.0-dev libatk1.0-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libc6-dev libcairo2-dev libdbus-1-dev libdbus-glib-1-dev libesd0-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgconf2-dev libgcrypt11-dev libgl1-mesa-dev libglade2-dev libglib2.0-dev libgnome-desktop-dev libgnome-keyring-dev libgnome-window-settings-dev libgnome2-dev libgnomecanvas2-dev libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgpg-error-dev libgtk2.0-dev libice-dev libidl-dev libjpeg62-dev liblzo-dev libopencdk8-dev liborbit2-dev libpango1.0-dev libpng12-dev libpopt-dev libselinux1-dev libsepol1-dev libsm-dev libstartup-notification0-dev libstdc++6-4.1-dev libtasn1-3-dev libwnck-dev libx11-dev libxau-dev libxcomposite-dev libxcomposite1 libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev libxres-dev libxt-dev linux-libc-dev m4 mesa-common-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-resource-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev && success) || failure 3 $?
    elif [ "$desktop_choice" = "1" ]; then
        (sudo apt-get --assume-yes --force-yes install autotools-dev binutils build-essential capplets-data cpp cpp-4.0 debconf-utils debhelper desktop-file-utils dpkg-dev g++ g++-4.0 gcc gcc-4.0 gconf2 gconf2-common gnome-control-center gnome-desktop-data gnome-icon-theme gnome-keyring gnome-menus gnome-mime-data html2text libart-2.0-dev libatk1.0-0 libatk1.0-dev libaudio-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev libavahi-glib1 libbonobo2-0 libbonobo2-common libbonobo2-dev libbonoboui2-0 libbonoboui2-common libbonoboui2-dev libc6-dev libcairo2-dev libcamel1.2-8 libcroco3 libdbus-1-dev libebook1.2-5 libedataserver1.2-7 libegroupwise1.2-9 libesd0-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgconf2-4 libgconf2-dev libgcrypt11-dev libgl1-mesa-dev libglade2-0 libglade2-dev libglib2.0-dev libglu1-mesa-dev libgnome-desktop-2 libgnome-desktop-dev libgnome-keyring-dev libgnome-keyring0 libgnome-menu2 libgnome2-0 libgnome2-common libgnome2-dev libgnomecanvas2-0 libgnomecanvas2-common libgnomecanvas2-dev libgnomeui-0 libgnomeui-common libgnomeui-dev libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-dev libgnutls-dev libgpg-error-dev libgsf-1-113 libgsf-1-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtk2.0-dev libice-dev libidl-dev libjpeg62-dev liblcms1-dev libmetacity0 libmng-dev libnautilus-extension1 libopencdk8-dev liborbit2-dev libpango1.0-0 libpango1.0-common libpango1.0-dev libpng12-dev libpopt-dev libqt4-core libqt4-dev libqt4-gui libqt4-qt3support libqt4-sql librsvg2-2 librsvg2-common libsm-dev libsoup2.2-8 libstartup-notification0-dev libstdc++6-4.0-dev libtasn1-2-dev libwnck-common libwnck-dev libwnck18 libx11-dev libxau-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxklavier10 libxml2-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxres-dev libxres1 libxt-dev linux-kernel-headers make mesa-common-dev pkg-config python-gmenu shared-mime-info x-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-resource-dev x11proto-xext-dev x11proto-xinerama-dev zlib1g-dev libavahi-client3 libavahi-common3 libc6 libc6-i686 libdbus-1-2 libfreetype6 libglib2.0-0 libgnutls12 libpng12-0 libpq4 libx11-6 && success) || failure 3 $?
fi
}

function xcb_support {
    if [ "$source_choice" = "0" ]; then
        echo_bold "Compiling libX11 compiled with xcb support..."

        cd $downdir
        [ -d libX11 ] && sudo rm -rf libX11
        mkdir libX11; cd libX11        

        wget http://ftp.debian.org/debian/pool/main/libx/libx11/libx11_1.1.3.orig.tar.gz
        wget http://ftp.debian.org/debian/pool/main/libx/libx11/libx11_1.1.3-1.diff.gz
        sudo apt-get --assume-yes --force-yes build-dep libx11-6
        tar xvf libx11_1.1.3.orig.tar.gz
        cd libX11-1.1.3
        sudo gunzip -c ../libx11_1.1.3-1.diff.gz | patch -p1
        sudo chmod +x debian/rules
        sudo debian/rules binary
        cd ..
        (sudo dpkg -i libx11*deb && success) || failure 4 $?
        sudo rm libx11*deb
        sudo rm libx11_1.1.3.orig.tar.gz
        sudo rm libx11_1.1.3-1.diff.gz
        sudo rm -rf libX11-1.1.3
    fi
}

function fusion {
    cd $downdir
    [ -d compiz ] && sudo rm -rf compiz

    case "$source_choice" in
        0)
            echo_bold "Downloading Compiz Fusion..."
            git clone git://git.freedesktop.org/git/xorg/app/compiz
            cd compiz; git checkout 0.6.0
            echo_bold "Installing Compiz Fusion..."
            (./autogen.sh --prefix=/usr/local --disable-$opdesktop && sudo make && sudo make install && success) || failure 5 $?
            export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
            ;;
        1)
            echo_bold "Downloading Compiz Fusion..."
            wget http://xorg.freedesktop.org/archive/individual/app/compiz-0.5.2.tar.gz
            tar xf compiz-0.5.2.tar.gz
            cd compiz-0.5.2; git checkout 0.6.0
            echo_bold "Installing Compiz Fusion..."
            (./configure --prefix=/usr/local --disable-$opdesktop && sudo make && sudo make install && success) || failure 5 $?
            export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
            ;;
    esac
}

function option_code_gen {
    cd $downdir
    [ -d bcop ] && sudo rm -rf bcop
    echo_bold "Downloading Compiz Fusion Option Code Generator..."
    git clone git://anongit.compiz-fusion.org/fusion/libraries/bcop
    cd bcop; git checkout 0.6.0
    echo_bold "Installing Compiz Fusion Option Code Generator..."
    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure 6 $?
}

function settings_lib {
    cd $downdir
    [ -d libcompizconfig ] && sudo rm -rf libcompizconfig
    echo_bold "Downloading the Settings Library for Plugins..."
    git clone git://anongit.compiz-fusion.org/fusion/compizconfig/libcompizconfig
    cd libcompizconfig; git checkout 0.6.0
    echo_bold "Installing the Settings Library for Plugins..."
    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure 7 $?
}

function compizconfig {
    cd $downdir
    [ -d compizconfig-python ] && sudo rm -rf compizconfig-python
    echo_bold "Downloading CompizConfig-Python..."
    git clone git://anongit.compiz-fusion.org/fusion/compizconfig/compizconfig-python
    cd compizconfig-python; git checkout 0.6.0
    echo_bold "Installing CompizConfig-Python..."
    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure 8 $?
}

function plugins_main {
    cd $downdir
    [ -d plugins-mai ] && sudo rm -rf plugins-main
    echo_bold "Downloading Compiz Fusion Plugins - Main..."
    git clone git://anongit.compiz-fusion.org/fusion/plugins-main
    cd plugins-main; git checkout 0.6.0
    echo_bold "Installing Compiz Fusion Plugins - Main..."
    (./autogen.sh && sudo make && sudo make install && success) || failure 10 $?
    cd $downdir
    git-clone git://anongit.opencompositing.org/fusion/plugins/3d
    cd 3d
    (sudo make && sudo make install && success) || failure

}

function plugins_extra {
    cd $downdir
    [ -d plugins-extra ] && sudo rm -rf plugins-extra
    echo_bold "Downloading Compiz Fusion Plugins - Extra..."
    git clone git://anongit.compiz-fusion.org/fusion/plugins-extra
    cd plugins-extra; git checkout 0.6.0
    echo_bold "Installing Compiz Fusion Plugins - Extra..."
    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure 11 $?
}

function plugins_unsupported {
    cd $downdir
    [ -d plugins-unsupported ] && sudo rm -rf plugins-unsupported
    echo_bold "Downloading Compiz Fusion Plugins - Unsupported..."
    git clone git://anongit.compiz-fusion.org/fusion/plugins-unsupported
    cd plugins-unsupported; git checkout 0.6.0
    echo_bold "Ins
talling Compiz Fusion Plugins - Unsupported..."
    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure 12 $?
}

function emerald {
    cd $downdir
    [ -d emerald ] && sudo rm -rf emerald
    echo_bold "Downloading Emerald..."
    git clone git://anongit.compiz-fusion.org/fusion/decorators/emerald
    cd emerald; git checkout 0.6.0
    echo_bold "Installing Emerald..."
    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure 13 $?
}

function emerald_themes {
    cd $downdir
    [ -d emerald-themes ] && sudo rm -rf emerald-themes
    echo_bold "Downloading a Package of Themes for Emerald..."
    git clone git://anongit.compiz-fusion.org/fusion/decorators/emerald-themes
    cd emerald-themes; git checkout 0.6.0
    echo_bold "Installing a Package of Themes for Emerald..."
    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure 14 $?
}

function settings_manager {
    cd $downdir
    [ -d ccsm ] && sudo rm -rf ccsm
    echo_bold "Downloading CompizConfig Settings Manager..."
    git clone git://anongit.compiz-fusion.org/fusion/compizconfig/ccsm
    cd ccsm
    echo_bold "Installing CompizConfig Settings Manager..."
    (sudo python setup.py install --prefix=/usr/local && success) || failure 9 $?
}

function fusion_icon {
    cd $downdir
    [ -d fusion-icon ] && sudo rm -rf fusion-icon
    echo_bold "Downloading Compiz Fusion Icon..."
    git clone git://anongit.compiz-fusion.org/users/crdlb/fusion-icon
    cd fusion-icon
    echo_bold "Installing Compiz Fusion Icon..."
    (sudo python setup.py install --prefix=/usr/local && success) || failure 15 $?
}

function nvidia {
    (sudo nvidia-xconfig --add-argb-glx-visuals -d 24 && success) || failure 16 $?
}

function update {

    cd $downdir
    if [ -d compiz ]; then
        cd compiz
	    git pull origin 0.6
	    (./autogen.sh --prefix=/usr/local --disable-$opdesktop && sudo make && sudo make install && success) || failure
	fi

    cd $downdir
    if [ -d bcop ]; then
	    cd bcop
	    git pull origin 0.6.0
        (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure
	fi

    cd $downdir
    if [ -d ccsm ]; then
	    cd ccsm
	    git pull origin 0.6.0
	    (sudo python setup.py install --prefix=/usr/local && success) || failure
	fi

    cd $downdir
    if [ -d compizconfig-python ]; then
	    cd compizconfig-python
	    git pull origin 0.6.0
	    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure 
	fi

    cd $downdir
    if [ -d emerald ]; then
	    cd emerald
	    git pull origin 0.6.0
	    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure
	fi

    cd $downdir
    if [ -d emerald-themes ]; then
	    cd emerald-themes
	    git pull origin 0.6.0
	    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure
	fi

    cd $downdir
    if [ -d libcompizconfig/ ]; then
	    cd libcompizconfig
	    git pull origin 0.6.0
	    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure
	fi

    cd $downdir
    if [ -d plugins-main ]; then
	    cd plugins-main
	    git pull origin 0.6.0
	    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure
	fi

    cd $downdir
    if [ -d plugins-extra ]; then
	    cd plugins-extra
	    git pull origin 0.6.0
	    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure
	fi

    cd $downdir
    if [ -d plugins-unsupported ]; then
	    cd plugins-unsupported
	   git pull origin 0.6.0
	    (./autogen.sh --prefix=/usr/local && sudo make && sudo make install && success) || failure
	fi

    cd $downdir
    if [ -d fusion-icon ]; then
	    cd fusion-icon
	    git pull origin 0.6.0
	    (sudo python setup.py install --prefix=/usr/local && success) || failure
	fi
}

function uninstall {

    cd $downdir
    if [ -d bcop ]; then
    	echo_bold "Uninstalling Compiz Fusion Option Code Generator..."
	    cd bcop
	    sudo make uninstall
    fi
	
    cd $downdir
    if [ -d ccsm ]; then
	    echo_bold "Uninstalling CompizConfig Settings Manager..."
	    cd ccsm
	    sudo python setup.py uninstall
    fi
	
    cd $downdir
    if [ -d compiz-0.5.2 ]; then
	    echo_bold "Uninstalling Compiz Fusion..."
	    cd compiz-0.5.2
	    sudo make uninstall
    fi
	
    cd $downdir
    if [ -d compizconfig-python ]; then
	    echo_bold "Uninstalling CompizConfig-Python..."
	    cd compizconfig-python
	    sudo make uninstall
    fi
	
    cd $downdir
    if [ -d emerald ]; then
	    echo_bold "Uninstalling Emerald..."
	    cd emerald
	    sudo make uninstall
    fi
	
    cd $downdir
    if [ -d emerald-themes ]; then
	    echo_bold "Uninstalling the Package of Themes for Emerald..."
	    cd emerald-themes
	    sudo make uninstall
    fi
	
    cd $downdir
    if [ -d fusion-icon ]; then
	    echo_bold "Uninstalling Compiz Fusion Icon..."
	    cd fusion-icon
	    sudo make uninstall
    fi
	
    cd $downdir
    if [ -d libcompizconfig ]; then
	    echo_bold "Uninstalling the Settings Library for Plugins..."
	    cd libcompizconfig
	    sudo make uninstall
    fi
	
    cd $downdir
    if [ -d plugins-extra ]; then
	    echo_bold "Uninstalling Compiz Fusion Plugins - Extra..."
	    cd plugins-extra
	    sudo make uninstall
    fi
	
    cd $downdir
    if [ -d plugins-main ]; then
	    echo_bold "Uninstalling Compiz Fusion Plugins - Main..."
	    cd plugins-main
	    sudo make uninstall
    fi
	
    cd $downdir
    if [ -d plugins-unsupported ]; then
	    echo_bold "Uninstalling Compiz Fusion Plugins - Unsupported..."
	    cd plugins-unsupported
	    sudo make uninstall
    fi
    
    cd $downdir; cd ..
    sudo rm -rf $downdir
    [ -d /usr/local/lib/compiz ] && sudo rm -rf /usr/local/lib/compiz
    [ -d /usr/local/share/compiz ] && sudo rm -rf /usr/local/share/compiz
    [ -d /usr/local/include/compiz ] && sudo rm -rf /usr/local/include/compiz
    [ -d /usr/share/compiz ] && sudo rm -rf /usr/share/compiz
    [ -d /usr/lib/compizconfig ] && sudo rm -rf /usr/lib/compizconfig
    [ -d /usr/lib/compiz ] && sudo rm -rf /usr/lib/compiz
    [ -d /usr/local/etc/compizconfig ] && sudo rm -rf /usr/local/etc/compizconfig
    [ -d /usr/local/lib/compizconfig ] && sudo rm -rf /usr/local/lib/compizconfig
    [ -d /usr/local/share/compizconfig ] && sudo rm -rf /usr/local/share/compizconfig
    [ -d /usr/share/compizconfig ] && sudo rm -rf /usr/share/compizconfig
    [ -d /etc/compizconfig ] && sudo rm -rf /etc/compizconfig
    
    [ -d $downdir ] || mkdir $downdir  # creates the directory if it doesn't exist
    cd $downdir

}

function answers {
    echo
    echo -e " \033[1mReminder:\033[0m You must have Main, Universe and Multiverse repositories enabled in" 
    echo " order this script to work properly (otherwise not everything needed will be"
    echo " able to be downloaded)."
    echo
    echo -e " \033[1mWarning:\033[0m If you get an error about libcairo.so.2 uninstall Mono and it will"
    echo " be solved (the version which is pre-installed in Ubuntu should not cause any"
    echo " problems)."
    echo
    echo -e " \033[1mWarning:\033[0m Do not delete the files that this script downloaded to your home"
    echo " folder. If you do so, future updates will not be possible."
    echo
    echo -e " \033[1mTip:\033[0m In order to launch Compiz Fusion and everything else needed, add"
    echo " fusion-icon to Sesisons."
    _pause
}

function deps {
    echo
    echo_bold " 0. Use (apt-get build-dep compiz)"
    echo " 1. Individual packages (apt-get install libgtk2.0-dev autotools-d...)"
    footer_n "How do you want get the dependancies? [0-1]: "
    read deps_choice
    case $deps_choice in 
        [01]) ;; 
        *) deps_choice=0 ;;
    esac
}

function source_source {
    echo
    echo_bold " 0. Git (developer's repository with latest source, unstable)"
    echo " 1. Stable (compiz-0.5.2)"
    footer_n "Which source do you want to use? [0-1]: "
    read source_choice
    case $source_choice in 
        [01]) ;; 
        *) source_choice=0 ;;
    esac
}

function desktop {
    echo
    echo_bold " 0. GNOME"
    echo " 1. KDE"
    footer_n "Which Desktop Environment are you currently using? [0-1]: "
    read desktop_choice
    case "$desktop_choice" in
        1) desktop="kde"; opdesktop="gnome" ;;
        *) desktop="gnome"; opdesktop="kde"; desktop_choice=0 ;;
    esac
}

function menu {
    while :; do
        header
        echo_bold " 0. Install..."
        echo " 1. Update"
        echo " 2. Uninstall"
        echo " 3. README"
        footer_n "Enter a number to start [0-3]:"
        read menu_choice
        case "$menu_choice" in
            1) [ `ls -1 $downdir | wc -l` -ne 0 ] && desktop && update; exit ;;
            2) uninstall; exit ;;
            3) answers ;;
            *) menu_choice=0; desktop; source_source; deps; install_menu; exit ;;
        esac
    done
}

function all {
    [ -d $downdir ] || mkdir $downdir  # creates the directory if it doesn't exist

    for i in 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16; do
        record[$i]="     \\033[1;32m[OK]\\033[0m"
    done

    remove_old
    uninstall
    req_deps
    compiz_deps
    xcb_support
    fusion
    option_code_gen
    settings_lib
    compizconfig
    settings_manager
    plugins_main
    plugins_extra
    plugins_unsupported
    emerald
    emerald_themes
    fusion_icon
}

function report {
   
    echo
    echo -e " * Installed Required Dependencies                          ${record[2]}"
    echo -e " * Installed Compiz' Dependencies                           ${record[3]}" 

    if [ "$source_choice" = "0" ]; then 
        echo -e " * Install libX11 with xcb support                          ${record[4]}"
    fi

    echo -e " * Installed Compiz Fusion                                  ${record[5]}"
    echo -e " * Installed Option Code Generator                          ${record[6]}"
    echo -e " * Installed Settings Library for Plugins                   ${record[7]}"
    echo -e " * Installed CompizConfig-Python                            ${record[8]}"
    echo -e " * Installed Settings Manager                               ${record[9]}"
    echo -e " * Installed Main Plugins                                   ${record[10]}"
    echo -e " * Installed Extra Plugins                                  ${record[11]}"
    echo -e " * Installed Unsupported Plugins                            ${record[12]}"
    echo -e " * Installed Emerald                                        ${record[13]}"
    echo -e " * Installed Emerald Themes                                 ${record[14]}"
    echo -e " * Installed Fusion-Icon                                    ${record[15]}"

    if [ $nvidia = "nvidia" ]; then
        echo -e " * Added argb-glx-visuals to xorg.conf                      ${record[16]}"
    fi

    echo
    echo -e "\\033[1;32mInstallation Completed!\\033[0m"
    echo
}

function install_menu {
    while :; do
        header
        echo_bold "  0. Full Installation (1-16)"
        echo "  1. Uninstall all previous versions (compiz/beryl/emerald)"
        echo "  2. Install Required Dependencies (git-core automake ...)"
        echo "  3. Install Compiz' Dependencies" 
        
        if [ "$source_choice" = "0" ]; then
            echo "  4. Install libX11 with xcb support (required for git)"
        else
            echo "  4. Install libX11 with xcb support (Skipping - for git only)"
        fi    

        echo "  5. Install Compiz Fusion"
        echo "  6. Install Option Code Generator"
        echo "  7. Install Settings Library for Plugins"
        echo "  8. Install CompizConfig-Python"
        echo "  9. Install Settings Manager"
        echo " 10. Install Main Plugins"
        echo " 11. Install Extra Plugins"
        echo " 12. Install Unsupported Plugins"
        echo " 13. Install Emerald"
        echo " 14. Install Emerald Themes"
        echo " 15. Install Fusion-Icon"

        if [ $nvidia = "nvidia" ]; then
            echo " 16. Add argb-glx-visuals to xorg.conf"
        else
            echo " 16. Add argb-glx-visuals to xorg.conf (Skipping - for NVIDIA only)"
        fi

        footer_n "Choose option [0-16]:"
        read install_menu_choice

        case "$install_menu_choice" in
            1) remove_old; uninstall; _pause ;;
            2) req_deps; _pause ;;
            3) compiz_deps; _pause ;;
            4) [ "$source_choice" = "0" ] && (xcb_support; _pause) ;;
            5) fusion; _pause ;;
            6) option_code_gen; _pause ;;
            7) settings_lib; _pause ;;
            8) compizconfig; _pause ;;
            9) settings_manager; _pause ;;
            10) plugins_main; _pause ;;
            11) plugins_extra; _pause ;;
            12) plugins_unsupported; _pause ;;
            13) emerald; _pause ;;
            14) emerald_themes; _pause ;;
            15) fusion_icon; _pause ;;
            16) [ $nvidia = "nvidia" ] && (nvidia; _pause) ;;
            *) all; report; exit ;;
        esac
    done
}


menu

```

---

