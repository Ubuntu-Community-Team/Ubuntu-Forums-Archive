---
title: "how to tightvncserver work on xubuntu"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by lance bermudez on 2008-02-18
using the web page at [http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html)
what im i doning wrong please help me

i have done the steps and installed
sudo apt-get install  xinetd tightvncserver ssh

service Xvnc
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = yes
user = root
server = /usr/bin/tightvncsrever
server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/home/lance/.vnc/passwd
port = 5901
}

# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=true
# Honor indirect queries, we run a chooser for these, and then redirect the
# user to the chosen host.  Otherwise we just log the user in locally.
HonorIndirect=false
# Maximum pending requests.
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time.
#MaxSessions=16
# Maximum wait times.
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single host.
# This is now set at 2 since if the server crashes then GDM doesn't know for
# some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way.
#Port=177
# Willing script, none is shipped and by default we'll send hostname system id.
# But if you supply something here, the output of this script will be sent as
# status of this host so that the chooser can display it.  You could for
# example send load, or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]
# The specific gtkrc file we use.  It should be the full path to the gtkrc that
# we need.  Unless you need a specific gtkrc that doesn't correspond to a
# specific theme, then just use the GtkTheme key.
#GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc

# The GTK+ theme to use for the GUI.
GtkTheme=Human
# If to allow changing the GTK+ (widget) theme from the greeter.  Currently
# this only affects the standard greeter as the graphical greeter does not yet
# have this ability.
#AllowGtkThemeChange=true
# Comma separated list of themes to allow.  These must be the names of the
# themes installed in the standard locations for gtk themes.  You can also
# specify 'all' to allow all installed themes.  These should be just the
# basenames of the themes such as 'Thinice' or 'LowContrast'.
#GtkThemesToAllow=all

# Maximum size of an icon, larger icons are scaled down.
#MaxIconWidth=128
#MaxIconHeight=128

[greeter]
# The following options for setting titlebar and setting window position are
# only useful for the standard login (gdmlogin) and are not used by the
# themed login (gdmgreeter).
#
# The standard login has a title bar that the user can move.
#TitleBar=true
# Don't allow user to move the standard login window.  Only makes sense if
# TitleBar is on.
#LockPosition=false
# Set a position for the standard login window rather then just centering the
# window.  If you enter negative values for the position it is taken as an
# offset from the right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0

# Enable the Face browser.  Note that the Browser key is only used by the
# standard login (gdmlogin) program.  The Face Browser is enabled in
# the Graphical greeter by selecting a theme that includes the Face
# Browser, such as happygnome-list.  The other configuration values that
# affect the Face Browser (MinimalUID, DefaultFace, Include, Exclude,
# IncludeAll, GlobalFaceDir) are used by both the Standard and Themed
# greeter.
Browser=true
# The default picture in the browser.
#DefaultFace=/usr/share/pixmaps/nobody.png
# User ID's less than the MinimalUID value will not be included in the face
# browser or in the gdmselection list for Automatic/Timed login.  They will not
# be displayed regardless of the settings for Include and Exclude.
MinimalUID=1000
# Users listed in Include will be included in the face browser and in the
# gdmsetup selection list for Automatic/Timed login.  Users should be separated
# by commas.
#Include=
# Users listed in Exclude are excluded from the face browser and from the
# gdmsetup selection list for Automatic/Timed login.  Excluded users will still
# be able to log in, but will have to type their username.  Users should be
# separated by commas.  
Exclude=nobody
# By default, an empty include list means display no users.  By setting
# IncludeAll to true, the password file will be scanned and all users will be
# displayed except users excluded via the Exclude setting and user ID's less
# than MinimalUID.  Scanning the password file can be slow on systems with
# large numbers of users and this feature should not be used in such
# environments.  The setting of IncludeAll does nothing if Include is set to a
# non-empty value.
IncludeAll=true
# If user or user.png exists in this dir it will be used as his picture.
#GlobalFaceDir=/usr/share/pixmaps/faces/

# File which contains the locale we show to the user.  Likely you want to use
# the one shipped with GDM and edit it.  It is not a standard locale.alias
# file, although GDM will be able to read a standard locale.alias file as well.
LocaleFile=/etc/gdm/locale.conf
# Logo shown in the standard greeter.
Logo=/usr/share/pixmaps/gdmDebianLogo.xpm
# Logo shown on file chooser button in gdmsetup (do not modify this value).
#ChooserButtonLogo=/usr/share/pixmaps/gdm-foot-logo.png
# The standard greeter should shake if a user entered the wrong username or
# password.  Kind of cool looking
#Quiver=true

# The Actions menu (formerly system menu) is shown in the greeter, this is the
# menu that contains reboot, shutdown, suspend, config and chooser.  None of
# these is available if this is off.  They can be turned off individually
# however.
#SystemMenu=true
# Configuration is available from the system menu of the greeter.
ConfigAvailable=false
# Should the chooser button be shown.  If this is shown, GDM can drop into
# chooser mode which will run the xdmcp chooser locally and allow the user to
# connect to some remote host.  Local XDMCP does not need to be enabled,
# however.
#ChooserButton=true

# Welcome is for all console logins and RemoteWelcome is for remote logins
# (through XDMCP).
# DefaultWelcome and DefaultRemoteWelcome set the string for Welcome to
# "Welcome" and for DefaultWelcome to "Welcome to %n", and properly translate
# the message to the appropriate language.  Note that %n gets translated to the
# hostname of the machine.  These default values can be overridden by setting
# DefaultWelcome and/or DefaultRemoteWelcome to false, and setting the Welcome
# and DefaultWelcome values as desired.  Just make sure the strings are in
# utf-8 Note to distributors, if you wish to have a different Welcome string
# and wish to have this translated you can have entries such as
# "Welcome[cs]=Vitejte na %n".
DefaultWelcome=true
DefaultRemoteWelcome=true
#Welcome=Welcome
#RemoteWelcome=Welcome to %n

# Xinerama screen we use to display the greeter on.  Not for true multihead,
# currently only works for Xinerama.
#XineramaScreen=0
# Background settings for the standard greeter:
# Type can be 0=None, 1=Image & Color, 2=Color, 3=Image
#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true
# The Standard greeter (gdmlogin) uses BackgroundColor as the background
# color, while the themed greeter (gdmgreeter) uses GraphicalThemedColor
# as the background color.
BackgroundColor=#dab082
GraphicalThemedColor=#dab082
# XDMCP session should only get a color, this is the sanest setting since you
# don't want to take up too much bandwidth
#BackgroundRemoteOnlyColor=true

# Program to run to draw the background in the standard greeter.  Perhaps
# something like an xscreensaver hack or some such.
#BackgroundProgram=
# If this is true then the background program is run always, otherwise it is
# only run when the BackgroundType is 0 (None).
#RunBackgroundProgramAlways=false
# Delay before starting background program
#BackgroundProgramInitialDelay=30
# Should the background program be restarted if it is exited.
#RestartBackgroundProgram=true
# Delay before restarting background program
#BackgroundProgramRestartDelay=30

# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
# example) and more failsafe then those supplied by scripts so distros should
# use this rather then just running an xterm from a script.
#ShowGnomeFailsafeSession=true
#ShowXtermFailsafeSession=true
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode
# where the session saving stuff is disabled in GDM
#ShowLastSession=true
# Always use 24 hour clock no matter what the locale.
#Use24Clock=auto
# Use circles in the password field.  Looks kind of cool actually, but only
# works with certain fonts.
UseCirclesInEntry=true
# Do not show any visible feedback in the password field. This is standard for
# instance in console, xdm and ssh.
#UseInvisibleInEntry=false

# These two keys are for the themed greeter (gdmgreeter).  Circles is the
# standard shipped theme.  If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true.  Otherwise use GraphicalTheme
# and specify just one theme.
GraphicalTheme=Human
#GraphicalThemes=bijou/:blueswirl/:circles/:debblue-list/:debblue/:ayo/:debian-dawn/:debian-greeter/:debian/:glassfoot/:hantzley/:happygnome/:industrial/:crystal/:linsta
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false

# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font to
# be used when displaying the contents of the file.
#InfoMsgFont=Sans 24

# If SoundOnLogin is true, then the greeter will beep when login is ready for
# user input.  If SoundOnLogin is a file and the greeter finds the 'play'
# executable (see daemon/SoundProgram) it will play that file instead of just
# beeping.
#SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav
# If SoundOnLoginSuccess, then the greeter will play a sound (as above) when a
# user successfully logs in.
#SoundOnLoginSuccess=false
#SoundOnLoginSuccessFile=
# If SoundOnLoginFailure, then the greeter will play a sound (as above) when a
# user fails to log in.
#SoundOnLoginFailure=false
#SoundOnLoginFailureFile=

# Specifies a program to be called by the greeter/login program when the
# initial screen is displayed.  The purpose is to provide a hook where files
# used after login can be preloaded to speed performance for the user. The
# program will only be called once only, the first time a greeter is displayed.
# The gdmprefetch command may be used.  This utility will load any libraries
# passed in on the command line, or if the argument starts with a "@"
# character, it will process the file assuming it is an ASCII file containing a
# list of libraries, one per line, and load each library in the file.
PreFetchProgram=/usr/lib/gdmprefetch @/etc/gdm/gdmprefetchlist

# The chooser is what's displayed when a user wants an indirect XDMCP session,
# or selects Run XDMCP chooser from the system menu
[chooser]
# Default image for hosts.
#DefaultHostImg=/usr/share/pixmaps/nohost.png
# Directory with host images, they are named by the hosts: host or host.png.
HostImageDir=/usr/share/hosts/
# Time we scan for hosts (well only the time we tell the user we are scanning
# actually, we continue to listen even after this has expired).
#ScanTime=4
# A comma separated lists of hosts to automatically add (if they answer to a
# query of course).  You can use this to reach hosts that broadcast cannot
# reach.
Hosts=
# Broadcast a query to get all hosts on the current network that answer.
Broadcast=true
# Set it to true if you want to send a multicast query to hosts.
Multicast=false
# It is an IPv6 multicast address.It is hardcoded here and will be replaced
# when officially registered xdmcp multicast address of TBD will be available.
#Multicast_Addr=ff02::1
# Allow adding random hosts to the list by typing in their names.
#AllowAdd=true

[debug]
# This will cause GDM to send debugging information to the system log, which 
# will create a LOT of output.  It is not recommended to turn this on for
# normal use, but it can be useful to determine the cause when GDM is not
# working properly.
Enable=false
# This will enable debug messages for accessibilty gesture listeners into the
# syslog.  This includes output about key events, mouse button events, and
# pointer motion events.  This is useful for figuring out the cause of why the
# gesture listeners may not be working, but is too verbose for general debug.
Gestures=false

# Attached DISPLAY Configuration
#
[servers]
# This section defines which attached DISPLAYS should be started by GDM by
# default.  You can add as many DISPLAYS as desired and they will always be
# started.  The key for each entry must be a unique number that cooresponds to
# the DISPLAY number to start the X server.  For a typical single-display
# machine, there will only be one entry "0" for DISPLAY ":0".  The first word
# in the value corresponds to an X server definition in the "X Server
# Definitions" section of the configuration file.  For example, the entry:
#
# 0=Standard
#
# Means that DISPLAY ":0" will start an X server as defined in the 
# [server-Standard] section.
#
# The optional device argument is used to specify the device that is associated
# with the DISPLAY.  When using Virtual Terminals (VT), this value is ignored
# and GDM will use the correct device name associated with the VT.  If not
# using VT, then GDM will use the value specified by this optional argument.
# If the device argument is not defined, then GDM will use the default setting
# for attached displays defined in the UtmpLineAttached configuration option.
# For the main display (typically DISPLAY ":0"), "/dev/console" is a reasonable
# value.  For other displays it is probably best to not include this argument
# unless you know the specific device associated with the DISPLAY.  The device
# value can contain "%d" which is translated to the DISPLAY value or %h which
# is translated to the hostname.
#
0=Standard device=/dev/console

# Example of how to set up DISPLAY :1 to also use Standard.
#1=Standard

# If you wish to run the XDMCP chooser on the local display use the following
# line
#0=Chooser

# X Server Definitions
#
# Note: Is your X server not listening to TCP requests?  Refer to the 
# security/DisallowTCP setting!

[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 
flexible=true
# Indicates that the X server should be started at a different process
# priority.  Values can be any integer value accepted by the setpriority C
# library function (normally between -20 and 20) with 0 being the default. For
# highly interactive applications, -5 yields good responsiveness. The default
# value is 0 and the setpriority function is not called if the value is 0.

#priority=0

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Terminal]
name=Terminal server
# Add -terminate to make things behave more nicely
command=/usr/bin/X -br -audit 0 -terminate
# Make this not appear in the flexible servers (we need extra params anyway,
# and terminate would be bad for xdmcp choosing).  You can make a terminal
# server flexible, but not with an indirect query.  If you need flexible
# indirect query server, then you must get rid of the -terminate and the only
# way to kill the flexible server will then be by Ctrl-Alt-Backspace.
flexible=false
# Do not handle this X server for attached displays.
handled=false

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Chooser]
name=Chooser server
command=/usr/bin/X -br -audit 0
# Make this not appear in the flexible servers for now, but if you wish to
# allow a chooser server then make this true.  This is the only way to make a
# flexible chooser server that behaves nicely.
flexible=false
# Run the chooser instead of the greeter.  When the user chooses a machine they
# will get this same server but run with "-terminate -query hostname".
chooser=true

[customcommand]
# This section allows you specify up to 10 custom commands. Each of the
# commands can be defined by the seven parameters listed below. In each of the
# descriptions of the parameters N can take on any values between 0 and 9,
# i.e. CustomCommand0=,CustomCommand1=,...,CustomCommand9=.  The  numbers
# can have gaps as long as they fit within predefined set of 10, and their
# placement order within this section and with respect to each other is
# not important.
#
# CustomCommandN, CustomCommandTextN, CustomCommandLabelN, 
# CustomCommandLRLabelN, CustomCommandTooltipN, CustomCommandIsPersistentN
# and CustomCommandNoRestartN should all be defined for a given integer N, 
# where N can be a number from 0-9 (if not the default values will be 
# assigned except CustomCommandN for which no default exists).

# Custom command to run.  Multiple commands may be specified separated by 
# semicolons.  GDM will use the first valid command.  Examples:
# /sbin/bootwindoze;/usr/bin/bootwindoze, or
# /sbin/runupdate;/usr/local/sbin/runupdate
#
#CustomCommandN=

# Custom command dialog message that will appear on all warning dialogs.
# This will vary depending on what you want to do. Examples:
# Are you sure you want to restart system into Windoze?, or
# Are you sure you want do do this?
#CustomCommandTextN=

# Custom command label that will appear as stock label on buttons/menu items.
# This option can't contain any semicolon characters (i.e. ";").
# Examples:
# _Windoze, or
# _Update Me
#CustomCommandLabelN=

# Custom command label that will appear as stock label on radio buttons/list
# items.  The underscore indicates the mnemonic used with this item.  Examples:
#   Restart into _Windoze
#   Perform system _Update
#CustomCommandLRLabelN=

# Custom command tooltip. Examples
# Restarts the computer into Windoze
# Updates the computer software to the most recent version(s)
#CustomCommandTooltipN=

# Custom command persistence option. Setting it to true will allow this
# command to appear outside the login manager, e.g. on the desktop through 
# Log Out/Shut Down dialogs. The default value is false.
#CustomCommandIsPersistentN=

# Custom command gdm/system restart option. Setting it to true will not
# restart gdm after command execution.  The default commands (reboot, shut
# down) all reboot the system by default which is why the default setting
# is true.
# In addition when corresponding CustomCommandIsPersistentN option is set to
# true, setting CustomCommandNoRestartN to false will place CustomCommandN
# in the Shut Down dialog set of actions, setting it to true will place
# CustomCommandN in the Log Out dialog set of actions.
#CustomCommandNoRestartN=
#
# Example layout for more than one command:
#CustomCommand0=
#CustomCommandText0=
#CustomCommandLabel0=
#CustomCommandLRLabel0=
#CustomCommandTooltip0=
#CustomCommandIsPersistent0=
#CustomCommandNoRestart0=
#
#CustomCommand1=
#CustomCommandText1=
#CustomCommandLabel1=
#CustomCommandLRLabel1=
#CustomCommandTooltip1=
#CustomCommandIsPersistent1=
#CustomCommandNoRestart1=
#
# and so on

---

### Post by lance bermudez on 2008-02-18
when trying to see my xubuntu form xubuntu i get
 
lance@xubuntu:~$ tightvncserver :1
tightvncserver: Wrong type or access mode of /home/lance/.vnc.

was able to get out to other computers  tell i did
lance@xubuntu:~$ sudo tightvncserver :1

New 'X' desktop is xubuntu:1

Starting applications specified in /home/lance/.vnc/xstartup
Log file is /home/lance/.vnc/xubuntu:1.log

lance@xubuntu:~$ vncviewer 192.168.1.47:5901

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

vncviewer: unable to open display ":0.0"

---

### Post by lance bermudez on 2008-02-18
restarted the computer and can now reach other computer again but im still getting the error 
failed to connect to server" on my wiindows 2000 box

---

### Post by bodhi.zazen on 2008-02-18
Try these links :

[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

---

### Post by lance bermudez on 2008-02-19
did i configure these right using this the web sites?

/usr/bin/vncserver do i need this one or should i edit the tightvncserver
______________________________________________________________________________________________________________________
#!/usr/bin/perl
#
#  Copyright (C) 2004-2006 Ola Lundqvist <opal@debian.org>
#  Copyright (C) 2002 Constantin Kaplinsky.  All Rights Reserved.
#  Copyright (C) 1999 AT&T Laboratories Cambridge.  All Rights Reserved.
#
#  This is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This software is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this software; if not, write to the Free Software
#  Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307,
#  USA.
#

#
# vncserver - wrapper script to start an X VNC server.
#

# This file was heavily edited by
#		Ola Lundqvist <opal@debian.org>
#               Marcus Brinkmann <Marcus.Brinkmann@ruhr-uni-bochum.de>
# Clean option by Dirk Eddelbuettel <edd@debian.org>

# Please report all errors to Debian and not to ORL.

#
# First make sure we're operating in a sane environment.
#

&SanityCheck();

#
# Global variables.  You may want to configure some of these for your site.
#

$geometry = "1024x768";
$depth = 24;
$desktopName = "X";
if (-d "/usr/share/tightvnc-java") {
    $vncClasses = "/usr/share/tightvnc-java";
}
$vncUserDir = "$ENV{HOME}/.vnc";
#$fontPath = "unix/:7100";

# Here is another example of setting the font path:
# $fontPath = "/usr/lib/X11/fonts/misc/,/usr/lib/X11/fonts/75dpi/";

# X colors database path is optional, uncomment and edit to use:
# $colorPath = "/usr/lib/X11/rgb";

# You might wish to make your vnc directory under /tmp, to make sure
# passwords are always kept on the local filesystem. To do that, just
# uncomment the line below. Note that in this case Xtightvnc's .Xauthority
# file will be searched in the same $vncUserDir directory by default,
# and $ENV{HOME}/.vncstartup will be executed instead of usual
# $vncUserDir/xstartup.
#
# $vncUserDir = "/tmp/$ENV{USER}-vnc";

$defaultXStartup
    = ("#!/bin/sh\n\n".
       "xrdb \$HOME/.Xresources\n".
       "xsetroot -solid grey\n".
       "x-terminal-emulator -geometry 80x24+10+10 -ls -title \"\$VNCDESKTOP Desktop\" &\n".
       "x-window-manager &\n");

$xauthorityFile = "$ENV{XAUTHORITY}";

######## Adding configuration possibility ################
$Config_file = "/etc/vnc.conf";
&ReadConfigFile();
$Config_file = "$ENV{HOME}/.vncrc";
&ReadConfigFile();

if (!$XFConfigPath) {
  foreach ("/etc/X11/xorg.conf", "/etc/X11/XF86Config-4", "/etc/X11/XF86Config" ){
      $XFConfigPath = $_;
      last if ( -e $XFConfigPath );
  }
}
if (!$fontPath) {
  &ReadXFConfigFont;
}
if (!$fontPath) {
  $fontPath = "/usr/X11R6/lib/X11/fonts/Type1/,".
              "/usr/X11R6/lib/X11/fonts/Speedo/,".
              "/usr/X11R6/lib/X11/fonts/misc/,".
              "/usr/X11R6/lib/X11/fonts/75dpi/,".
              "/usr/X11R6/lib/X11/fonts/100dpi/,".
              "/usr/share/fonts/X11/misc/,".
      	      "/usr/share/fonts/X11/Type1/,".
              "/usr/share/fonts/X11/75dpi/,".
              "/usr/share/fonts/X11/100dpi/".
	      "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,".
	      "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
}
if (!$colorPath) {
  &ReadXFConfigColor;
}
if (!$colorPath) {
  foreach ("/etc/X11/rgb", "/usr/share/X11/rgb", "/usr/X11R6/lib/X11/rgb"){
      $colorPath = $_;
      last if ( -e "${colorPath}.txt" );
  }
}

##########################################################

$vncUserDirUnderTmp = ($vncUserDir =~ m|^/tmp/.+|) ? 1 : 0;
$xstartup = ($vncUserDirUnderTmp) ?
  "$ENV{HOME}/.vncstartup" : "$vncUserDir/xstartup";
$xstartup = $vncStartup if ($vncStartup);

unless ($xauthorityFile) {
    if ($vncUserDirUnderTmp) {
        $xauthorityFile = "$vncUserDir/.Xauthority";
    } else {
        $xauthorityFile = "$ENV{HOME}/.Xauthority";
    }
}

chop($host = `uname -n`);


# Check command line options

&ParseOptions("-geometry",1,"-depth",1,"-pixelformat",1,"-name",1,"-kill",1,
	      "-help",0,"-h",0,"--help",0,
	      "-clean",0, "-fp",1,
	      "-alwaysshared",0, "-nevershared",0,
	      "-httpport",1,"-basehttpport",1);

&Usage() if ($opt{'-help'} || $opt{'-h'} || $opt{'--help'});

&Kill() if ($opt{'-kill'});

$useClasses = 0;
if (defined $vncClasses) {
  if(! -d $vncClasses) {
    die "VNC class files can not be found at $vncClasses.";
  }
  $useClasses = 1;
}

# Uncomment this line if you want default geometry, depth and pixelformat
# to match the current X display:
# &GetXDisplayDefaults();

if ($opt{'-geometry'}) {
    $geometry = $opt{'-geometry'};
}
if ($opt{'-depth'}) {
    $depth = $opt{'-depth'};
    $pixelformat = "";
}
if ($opt{'-pixelformat'}) {
    $pixelformat = $opt{'-pixelformat'};
}

if ($opt{'-fp'}) {
    @fontPathElements = split(/\s*,\s*/, "$opt{'-fp'}");

    $fontPath = '';

    foreach $i (0.."$#fontPathElements") {
	$tempFontPath = $fontPathElements[$i];
	if ($tempFontPath !~ m!^[^/]*/[^/]*:\d+$!) {
	    $tempFontPath =~ s/:unscaled$//;
	    if (-r "$tempFontPath/fonts.dir") {
		$fontPath .= "$fontPathElements[$i],";
	    }
	} else {
	    $fontPath .= "$fontPathElements[$i],";
	}
    }
    chop $fontPath;
}

&CheckGeometryAndDepth();

if ($opt{'-name'}) {
    $desktopName = $opt{'-name'};
}

# Create the user's vnc directory if necessary.

unless (-e $vncUserDir) {
    unless (mkdir($vncUserDir, 0700)) {
        die "$prog: Could not create $vncUserDir.\n";
    }
}
($z,$z,$mode) = lstat("$vncUserDir");
if (!-d _ || !-o _ || ($vncUserDirUnderTmp && ($mode & 0777) != 0700)) {
    die "$prog: Wrong type or access mode of $vncUserDir.\n";
}

# Make sure the user has a password.

($z,$z,$mode) = lstat("$vncUserDir/passwd");
if (-e _ && (!-f _ || !-o _)) {
    die "$prog: Wrong type or ownership on $vncUserDir/passwd.\n";
}
if (!-e _ || ($mode & 077) != 0) {
    warn "\nYou will require a password to access your desktops.\n\n";
    system("vncpasswd $vncUserDir/passwd");
    if (($? & 0xFF00) != 0) {
        exit 1;
    }
}

# Find display number.

if ((@ARGV > 0) && ($ARGV[0] =~ /^:(\d+)$/)) {
    $displayNumber = $1;
    shift(@ARGV);
    unless (&CheckDisplayNumber($displayNumber)) {
	die "A VNC server is already running as :$displayNumber\n";
    }
} elsif ((@ARGV > 0) && ($ARGV[0] !~ /^-/)) {
    &Usage();
} else {
    $displayNumber = &GetDisplayNumber();
}

$vncPort = 5900 + $displayNumber;

$desktopLog = "$vncUserDir/$host:$displayNumber.log";
unlink($desktopLog);

# Make an X server cookie - use as the seed the sum of the current time, our
# PID and part of the encrypted form of the password.  Ideally we'd use
# /dev/urandom, but that's only available on Linux.

srand(time+$$+unpack("L",`cat $vncUserDir/passwd`));
$cookie = "";
for (1..16) {
    $cookie .= sprintf("%02x", int(rand(256)));
}

system("xauth -f $xauthorityFile add $host:$displayNumber . $cookie");
system("xauth -f $xauthorityFile add $host/unix:$displayNumber . $cookie"); 

# Now start the X VNC Server

$cmd = "Xtightvnc :$displayNumber";
$cmd .= " -desktop " . &quotedString($desktopName);
if ($useClasses) {
  $cmd .= " -httpd $vncClasses";
  print ("Found $vncClasses for http connections.\n");
  if ($opt{'-httpport'}) {
    $cmd .= " -httpport $opt{'-httpport'}";
    print ("Listening to $opt{'-httpport'} for http connections.\n");
  }
  elsif ($opt{'-basehttpport'}) {
    my $v = $opt{'-basehttpport'} + $displayNumber;
    print ("Listening to $v for http connections.\n");
    $cmd .= " -httpport $v";
  }
}
$cmd .= " -auth $xauthorityFile";
$cmd .= " -geometry $geometry" if ($geometry);
$cmd .= " -depth $depth" if ($depth);
$cmd .= " -pixelformat $pixelformat" if ($pixelformat);
$cmd .= " -rfbwait 120000";
$cmd .= " -rfbauth $vncUserDir/passwd";
$cmd .= " -rfbport $vncPort";
$cmd .= " -fp $fontPath" if ($fontPath);
$cmd .= " -co $colorPath" if ($colorPath);
$cmd .= " -alwaysshared" if ($opt{'-alwaysshared'});
$cmd .= " -nevershared" if ($opt{'-nevershared'});

foreach $arg (@ARGV) {
    $cmd .= " " . &quotedString($arg);
}
$cmd .= " >> " . &quotedString($desktopLog) . " 2>&1";

# Run $cmd and record the process ID.

$pidFile = "$vncUserDir/$host:$displayNumber.pid";
system("$cmd & echo \$! >$pidFile");

# Give Xtightvnc a chance to start up

sleep(1);
unless (kill 0, `cat $pidFile`) {
    warn "Couldn't start Xtightvnc; trying default font path.\n";
    warn "Please set correct fontPath in the $prog script.\n";
    $cmd =~ s@-fp [^ ]+@@;
    system("$cmd & echo \$! >$pidFile");
    sleep(1);
}
unless (kill 0, `cat $pidFile`) {
    warn "Couldn't start Xtightvnc process.\n\n";
    open(LOG, "<$desktopLog");
    while (<LOG>) { print; }
    close(LOG);
    die "\n";
}

warn "\nNew '$desktopName' desktop is $host:$displayNumber\n\n";

# Create the user's xstartup script if necessary.

unless (-e "$xstartup") {
    warn "Creating default startup script $xstartup\n";
    open(XSTARTUP, ">$xstartup");
    print XSTARTUP $defaultXStartup;
    close(XSTARTUP);
    chmod 0755, "$xstartup";
}

# Run the X startup script.

warn "Starting applications specified in $xstartup\n";
warn "Log file is $desktopLog\n\n";

# If the unix domain socket exists then use that (DISPLAY=:n) otherwise use
# TCP (DISPLAY=host:n)

if (-e "/tmp/.X11-unix/X$displayNumber") {
    $ENV{DISPLAY}= ":$displayNumber";
} else {
    $ENV{DISPLAY}= "$host:$displayNumber";
}
$ENV{VNCDESKTOP}= $desktopName;

system("$xstartup >> " . &quotedString($desktopLog) . " 2>&1 &");

exit;


############################ Debian functions #################################
# I thank Manoj for the code below.
#
# ReadConfigFile reads in a config file and sets variables according to it.
#

sub ReadConfigFile
{
  open(CONFIG, "$Config_file") || return;
  my $lineno = 0;
  while (<CONFIG>) {
      chomp;
      $lineno++;
      s/\#.*//og;
      next if /^\s*$/og;
      $_ .= ";" unless /;\s*$/;
      if (/^\s*([^=]+)\s*=\s*(\S.*)$/o) {
          my $ret = eval "$1=$2";
          if ($@) {
              print STDERR "Error parsing config file $Config_file!\n";
              print STDERR "$lineno:$_\n";
          }
      }
  }
}

sub ReadXFConfigFont
{
  open(CONFIG, "$XFConfigPath") || return;
  my $lineno = 0;
  while (<CONFIG>) {
      chomp;
      $lineno++;
      s/\#.*//og;
      next if /^\s*$/og;
      if (/^\s*FontPath\s*"(\S.*)"\s*$/o) {
          $fontPath .= "," if $fontPath;
          $fontPath .= $1;
      }
  }
}

sub ReadXFConfigColor
{
  open(CONFIG, "$XFConfigPath") || return;
  my $lineno = 0;
  while (<CONFIG> && !$colorPath) {
      chomp;
      $lineno++;
      s/\#.*//og;
      next if /^\s*$/og;
      if (/^\s*RgbPath\s*"(\S.*)"\s*$/o) {
          $colorPath = $1;
      }
  }
}


########## End of debian functions ###########

###############################################################################
#
# CheckGeometryAndDepth simply makes sure that the geometry and depth values
# are sensible.
#

sub CheckGeometryAndDepth
{
    if ($geometry =~ /^(\d+)x(\d+)$/) {
	$width = $1; $height = $2;

	if (($width<1) || ($height<1)) {
	    die "$prog: geometry $geometry is invalid\n";
	}

	while (($width % 4)!=0) {
	    $width = $width + 1;
	}

	while (($height % 2)!=0) {
	    $height = $height + 1;
	}

	$geometry = "${width}x$height";
    } else {
	die "$prog: geometry $geometry is invalid\n";
    }

    if (($depth < 8) || ($depth > 32)) {
	die "Depth must be between 8 and 32\n";
    }
}


#
# GetDisplayNumber gets the lowest available display number.  A display number
# n is taken if something is listening on the VNC server port (5900+n) or the
# X server port (6000+n).
#

sub GetDisplayNumber
{
    foreach $n (1..99) {
	if (&CheckDisplayNumber($n)) {
	    return $n+0; # Bruce Mah's workaround for bug in perl 5.005_02
	}
    }
    
    die "$prog: no free display number on $host.\n";
}


#
# CheckDisplayNumber checks if the given display number is available.  A
# display number n is taken if something is listening on the VNC server port
# (5900+n) or the X server port (6000+n).
#

sub CheckDisplayNumber
{
    local ($n) = @_;

    socket(S, $AF_INET, $SOCK_STREAM, 0) || die "$prog: socket failed: $!\n";
    eval 'setsockopt(S, &SOL_SOCKET, &SO_REUSEADDR, pack("l", 1))';
    unless (bind(S, pack('S n x12', $AF_INET, 6000 + $n))) {
	close(S);
	return 0;
    }
    close(S);

    socket(S, $AF_INET, $SOCK_STREAM, 0) || die "$prog: socket failed: $!\n";
    eval 'setsockopt(S, &SOL_SOCKET, &SO_REUSEADDR, pack("l", 1))';
    unless (bind(S, pack('S n x12', $AF_INET, 5900 + $n))) {
	close(S);
	return 0;
    }
    close(S);

    if (-e "/tmp/.X$n-lock") {
	warn "\nWarning: $host:$n is taken because of /tmp/.X$n-lock\n";
	warn "Remove this file if there is no X server $host:$n\n";
	return 0;
    }

    if (-e "/tmp/.X11-unix/X$n") {
	warn "\nWarning: $host:$n is taken because of /tmp/.X11-unix/X$n\n";
	warn "Remove this file if there is no X server $host:$n\n";
	return 0;
    }

    return 1;
}


#
# GetXDisplayDefaults uses xdpyinfo to find out the geometry, depth and pixel
# format of the current X display being used.  If successful, it sets the
# options as appropriate so that the X VNC server will use the same settings
# (minus an allowance for window manager decorations on the geometry).  Using
# the same depth and pixel format means that the VNC server won't have to
# translate pixels when the desktop is being viewed on this X display (for
# TrueColor displays anyway).
#

sub GetXDisplayDefaults
{
    local (@lines, @matchlines, $width, $height, $defaultVisualId, $i,
	   $red, $green, $blue);

    $wmDecorationWidth = 4;	# a guess at typical size for window manager
    $wmDecorationHeight = 24;	# decoration size

    return unless (defined($ENV{DISPLAY}));

    @lines = `xdpyinfo 2>/dev/null`;

    return if ($? != 0);

    @matchlines = grep(/dimensions/, @lines);
    if (@matchlines) {
	($width, $height) = ($matchlines[0] =~ /(\d+)x(\d+) pixels/);

	$width -= $wmDecorationWidth;
	$height -= $wmDecorationHeight;

	$geometry = "${width}x$height";
    }

    @matchlines = grep(/default visual id/, @lines);
    if (@matchlines) {
	($defaultVisualId) = ($matchlines[0] =~ /id:\s+(\S+)/);

	for ($i = 0; $i < @lines; $i++) {
	    if ($lines[$i] =~ /^\s*visual id:\s+$defaultVisualId$/) {
		if (($lines[$i+1] !~ /TrueColor/) ||
		    ($lines[$i+2] !~ /depth/) ||
		    ($lines[$i+4] !~ /red, green, blue masks/))
		{
		    return;
		}
		last;
	    }
	}

	return if ($i >= @lines);

	($depth) = ($lines[$i+2] =~ /depth:\s+(\d+)/);
	($red,$green,$blue)
	    = ($lines[$i+4]
	       =~ /masks:\s+0x([0-9a-f]+), 0x([0-9a-f]+), 0x([0-9a-f]+)/);

	$red = hex($red);
	$green = hex($green);
	$blue = hex($blue);

	if ($red > $blue) {
	    $red = int(log($red) / log(2)) - int(log($green) / log(2));
	    $green = int(log($green) / log(2)) - int(log($blue) / log(2));
	    $blue = int(log($blue) / log(2)) + 1;
	    $pixelformat = "rgb$red$green$blue";
	} else {
	    $blue = int(log($blue) / log(2)) - int(log($green) / log(2));
	    $green = int(log($green) / log(2)) - int(log($red) / log(2));
	    $red = int(log($red) / log(2)) + 1;
	    $pixelformat = "bgr$blue$green$red";
	}
    }
}


#
# quotedString returns a string which yields the original string when parsed
# by a shell.
#

sub quotedString
{
    local ($in) = @_;

    $in =~ s/\'/\'\"\'\"\'/g;

    return "'$in'";
}


#
# removeSlashes turns slashes into underscores for use as a file name.
#

sub removeSlashes
{
    local ($in) = @_;

    $in =~ s|/|_|g;

    return "$in";
}


#
# Usage
#

sub Usage
{
    die("TightVNC server version 1.2.9\n".
	"\n".
	"Usage: $prog [<OPTIONS>] [:<DISPLAY#>]\n".
	"       $prog -kill :<DISPLAY#>\n".
	"\n".
	"<OPTIONS> are Xtightvnc options, or:\n".
	"\n".
	"        -name <DESKTOP-NAME>\n".
	"        -depth <DEPTH>\n".
	"        -geometry <WIDTH>x<HEIGHT>\n".
	"        -httpport number\n".
	"        -basehttpport number\n".
	"        -alwaysshared\n".
	"        -nevershared\n".
	"        -pixelformat rgb<NNN>\n".
	"        -pixelformat bgr<NNN>\n".
	"\n".
	"See tightvncserver and Xtightvnc manual pages for more information.\n");
}


#
# Kill
#

sub Kill
{
    $opt{'-kill'} =~ s/(:\d+)\.\d+$/$1/; # e.g. turn :1.0 into :1

    if ($opt{'-kill'} =~ /^:\d+$/) {
	$pidFile = "$vncUserDir/$host$opt{'-kill'}.pid";
    } else {
	if ($opt{'-kill'} !~ /^$host:/) {
	    die "\nCan't tell if $opt{'-kill'} is on $host\n".
		"Use -kill :<number> instead\n\n";
	}
	$pidFile = "$vncUserDir/$opt{'-kill'}.pid";
    }

    unless (-r $pidFile) {
	die "\nCan't find file $pidFile\n".
	    "You'll have to kill the Xtightvnc process manually\n\n";
    }

    $SIG{'HUP'} = 'IGNORE';
    chop($pid = `cat $pidFile`);
    warn "Killing Xtightvnc process ID $pid\n";
    system("kill $pid");
    unlink $pidFile;

    ## If option -clean is given, also remove the logfile
    unlink "$vncUserDir/$host$opt{'-kill'}.log" if ($opt{'-clean'});

    exit;
}


#
# ParseOptions takes a list of possible options and a boolean indicating
# whether the option has a value following, and sets up an associative array
# %opt of the values of the options given on the command line. It removes all
# the arguments it uses from @ARGV and returns them in @optArgs.
#

sub ParseOptions
{
    local (@optval) = @_;
    local ($opt, @opts, %valFollows, @newargs);

    while (@optval) {
	$opt = shift(@optval);
	push(@opts,$opt);
	$valFollows{$opt} = shift(@optval);
    }

    @optArgs = ();
    %opt = ();

    arg: while (defined($arg = shift(@ARGV))) {
	foreach $opt (@opts) {
	    if ($arg eq $opt) {
		push(@optArgs, $arg);
		if ($valFollows{$opt}) {
		    if (@ARGV == 0) {
			&Usage();
		    }
		    $opt{$opt} = shift(@ARGV);
		    push(@optArgs, $opt{$opt});
		} else {
		    $opt{$opt} = 1;
		}
		next arg;
	    }
	}
	push(@newargs,$arg);
    }

    @ARGV = @newargs;
}


#
# Routine to make sure we're operating in a sane environment.
#

sub SanityCheck
{
    local ($cmd);

    #
    # Get the program name
    #

    ($prog) = ($0 =~ m|([^/]+)$|);

    #
    # Check we have all the commands we'll need on the path.
    #

 cmd:
    foreach $cmd ("uname","xauth","Xtightvnc","vncpasswd") {
	for (split(/:/,$ENV{PATH})) {
	    if (-x "$_/$cmd") {
		next cmd;
	    }
	}
	die "$prog: couldn't find \"$cmd\" on your PATH.\n";
    }

    #
    # Check the HOME and USER environment variables are both set.
    #

    unless (defined($ENV{HOME})) {
	die "$prog: The HOME environment variable is not set.\n";
    }
    unless (defined($ENV{USER})) {
	die "$prog: The USER environment variable is not set.\n";
    }

    #
    # Find socket constants. 'use Socket' is a perl5-ism, so we wrap it in an
    # eval, and if it fails we try 'require "sys/socket.ph"'.  If this fails,
    # we just guess at the values.  If you find perl moaning here, just
    # hard-code the values of AF_INET and SOCK_STREAM.  You can find these out
    # for your platform by looking in /usr/include/sys/socket.h and related
    # files.
    #

    chop($os = `uname`);
    chop($osrev = `uname -r`);

    eval 'use Socket';
    if ($@) {
	eval 'require "sys/socket.ph"';
	if ($@) {
	    if (($os eq "SunOS") && ($osrev !~ /^4/)) {
		$AF_INET = 2;
		$SOCK_STREAM = 2;
	    } else {
		$AF_INET = 2;
		$SOCK_STREAM = 1;
	    }
	} else {
	    $AF_INET = &AF_INET;
	    $SOCK_STREAM = &SOCK_STREAM;
	}
    } else {
	$AF_INET = &AF_INET;
	$SOCK_STREAM = &SOCK_STREAM;
    }
}




______________________________________________________________________________________________________________________

here is /etc/vnc.conf configurtion

# /etc/vnc.conf written by Marcus Brinkmann. This file is in the Public Domain.
#
# This is the configuration file for the vncserver package.
# It is perl syntax, but only variable assignment is allowed.
# A semicolon will be added if missing.
# Every value has suitable defaults, so you probably don't need any file.
#
# This file will be sourced by `vncserver' and `vncpasswd'.
# After this file, $(HOME)/.vncrc will be sourced, so values can be
# overwritten on a per-user basis. If you want to reactivate the default
# value there, you have to specify an empty value. For example, $fontPath
# will set to the default value after
#
# $fontPath = "/foo";
# $fontPath = "";
#
# If you are missing something, please let me know.
# [email]Marcus.Brinkmann@ruhr-uni-bochum.de[/email]

# System configuration
# --------------------
#
# This section contains entries that should be true for all users.

# $vncClasses should be the path to the java classes of server.
# $vncClasses = "/usr/share/vncserver";

# $XFConfigPath   can be set to the global XF86Config file. This will be
#                 parsed to gain default values for $fontPath and $colorPath.
#                 If you want to disable this feature, point it to an
#                 invalid file, "/foo" for example.
# $XFConfigPath = "/etc/X11/XF86Config";

# $fontPath should be a comma seperated list of fonts to be added to the font
#           path. If not specified, and $XFConfigPath is valid, vncserver
#           will read the $fontPath from there. If both are not set, the
#           default will apply.
# Example: $fontPath = "tcp/localhost:7100";     # would make vnc to use xfs.
# Example: $fontPath = "";
#	$fontPath .= "/usr/X11R6/lib/X11/fonts/misc/,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/Type1/,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/Speedo/,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/75dpi/,";
# 	$fontPath .= "/usr/X11R6/lib/X11/fonts/100dpi/,";
#	$fontPath .= "/usr/X11R6/lib/X11/fonts/freefont/,";
#	$fontPath .= "/usr/X11R6/lib/X11/fonts/sharefont/";
# I don't know what the default is, though.

# $colorPath should be the RGB file to be used by X. This can also be taken from
#            XF86Config file if specified by $XFConfigPath
# $colorPath = "/usr/X11R6/lib/X11/rgb";

# User configuration
# ------------------
#
# This section contains entries that may change from user to user.

# $vncUserDir contains the filename for the log files directory of Xvnc
#             (the server) and the viewers that are connected to it.
# $vncUserDir = "$ENV{HOME}/.vnc";

# $vncPasswdFile contains the filename of the password file for Xvnc.
# $vncPasswdFile = $vncUserDir . "/passwd";

# $vncStartup points to a script that will be started at the very beginning.
# $vncStartup = "/etc/X11/Xsession";

# $xauthorityFile should be the path to the authority file that should be used
#                 by your vnc X server.
# $xauthorityFile = "$ENV{HOME}/.Xauthority";

# $defaultDesktopName should be set to the default name of the desktop.
#                     This can be changed at the command line with -name.
# $defaultDesktopName = "X";

# $geometry sets framebuffer width & height. Default will be calculated if
#           server is started from within a running X servers. Can be changed at
#           the commandline (-geometry). A fixed default will be used if
#           vncserver is not invoked in a running X session.
# Example:  $geometry ="640x480";

# $depth       sets the framebuffer color depth. Must be between 8 and 32.
# $pixelformat sets the default pixelformat.
#              The default will be calculated if none of both is specified
#              and when vncserver is called from within a running X servers.
#              Can be changed at the command line with option -depth.
#              A fixed default value will be used if vncserver is not
#              invoked in a running X session.
# Example:  $depth = "16";
#           $pixelformat = "rgb565";

# $getDefaultFrom sets the display from which you can query the default of
#                 the above three options, if you don't want to start vncserver
#                 from within a running X server. It will be added to the call
#                 of xdpyinfo.
#                 It is useful to get the default from the X server you will
#                 run xvncviewer in.
# Example:  $getDefaultFrom = "-display localhost:0"

# $rfbwait sets the maximum time in msec to wait for vnc client viewer.
# $rfbwait = "120000";

$fontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
$fontPath .= "/usr/share/X11/fonts/misc,";
$fontPath .= "/usr/share/X11/fonts/cyrillic,";
$fontPath .= "/usr/share/X11/fonts/100dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/75dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/Type1,";
$fontPath .= "/usr/share/X11/fonts/CID,";
$fontPath .= "/usr/share/X11/fonts/100dpi,";
$fontPath .= "/usr/share/X11/fonts/75dpi,";
# paths to defoma fonts
$fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,";
$fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID";

______________________________________________________________________________________________________________________

where would i put the link to the password which is in my /home/lance/.vnc folder called passwd

##!/bin/sh

xrdb $HOME/.Xresources
#xsetroot -solid navy # Choose your color
xfwm4 2> /dev/null &
#x-window-manager &
xfce4-panel 2> /dev/null &
#gnome-panel 2> /dev/null &
xfce4-terminal &
#xterm &

should this be change from xfce4-terminal to gnome-terminal. i had to switch becuse when i started xfce4-terminal the computer would make me relog in each time i started a xfce4-terminal. i did not uninstall xfce4-terminal when i installed gnome-terminal
__________________________________________________________________________________________________________________

---

### Post by bodhi.zazen on 2008-02-19
If you please :

1. If you must post long config files, please post them as attachments (test files).

2. What is your question regarding the config files you are posting ? They look like the standard default config files to me.

3. What problem are you having ? The only one I understood is with your terminal. Yea, if you gnome, use gnome-terminal.

---

### Post by lance bermudez on 2008-02-20
the files ate not the default i have made changes but want to know if i made them right using the websites listed. where would i put the link to the password which is in my /home/lance/.vnc folder called passwd in the /etc/vnc.config file. with the startup script in /home/lance/.vnc is below

---

