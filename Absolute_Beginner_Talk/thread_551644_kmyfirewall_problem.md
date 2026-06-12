---
title: "kmyfirewall problem"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by fiskking on 2007-09-15
after installing KMyfirewall, I then went into terminal and entered ¨ sudo kmyfirewall¨.  after starting the following errors were given:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
kio (KService*): WARNING: Invalid Service : /usr/share/applications/kde/kmyfirewall.desktop
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
kmyfirewall: 
Found Splashscreen at: /usr/share/apps/kmyfirewall/pics/splash.png
kmyfirewall: KMFSelectInterface::accept()
kmyfirewall: Found item: 0
kmyfirewall: 
Found Splashscreen at: /usr/share/apps/kmyfirewall/pics/splash.png
kmyfirewall: 
void KMFConfigDialog::setupPlugins()
kmyfirewall: void KMFConfigDialog::checkPlugins()
kmyfirewall: 
Start query
kmyfirewall: Query performed for KMyFirewall/Installer
kmyfirewall: Found Plugin: KMyFirewall Installer for Linux
Library: libkmfinstaller_linux
kmyfirewall: Query performed for KMyFirewall/Compiler
kmyfirewall: Found Plugin: KMyFirewall IPTables Compiler
Library: libkmfcompiler_ipt
kmyfirewall: 
kmyfirewall: Calling Constuctor: KMFCompilerInterface::KMFCompilerInterface()
kmyfirewall: ERROR: Couldn't find main API
kmyfirewall: Returning Compiler Plugin.
kmyfirewall: KMFConfigDialog::registerCompiler: OS: Linux Backend: IPTables
kmyfirewall: Query performed for KMyFirewall/RuleOptionEdit
kmyfirewall: Found Plugin: KMyFirewall Protocol option edit
Library: libkmfruleoptionedit_protocol
kmyfirewall: Found Plugin: KMyFirewall Interface option edit
Library: libkmfruleoptionedit_interface
kmyfirewall: Found Plugin: KMyFirewall Tos option edit
Library: libkmfruleoptionedit_tos
kmyfirewall: Found Plugin: KMyFirewall IP option edit
Library: libkmfruleoptionedit_ip
kmyfirewall: Found Plugin: KMyFirewall Limit option edit
Library: libkmfruleoptionedit_limit
kmyfirewall: Found Plugin: KMyFirewall MAC option edit
Library: libkmfruleoptionedit_mac
kmyfirewall: Found Plugin: KMyFirewall Custom option edit
Library: libkmfruleoptionedit_custom
kmyfirewall: Found Plugin: KMyFirewall State option edit
Library: libkmfruleoptionedit_state
kmyfirewall: Query performed for KMyFirewall/RuleTargetOptionEdit
kmyfirewall: Found Plugin: KMyFirewall TOS option edit
Library: libkmfruletargetoptionedit_tos
kmyfirewall: Found Plugin: KMyFirewall NAT option edit
Library: libkmfruletargetoptionedit_nat
kmyfirewall: Found Plugin: KMyFirewall LOG target option edit
Library: libkmfruletargetoptionedit_log
kmyfirewall: Found Plugin: KMyFirewall MARK option edit
Library: libkmfruletargetoptionedit_mark
kmyfirewall: found Interfaces (lo)
kmyfirewall: Found Distributionsysv
kmyfirewall: void KMFConfigDialog::slotEnableGentooMode( bool enable )
kmyfirewall: void KMFConfigDialog::slotSlackwareMode( bool enable )
kmyfirewall: Found item: Linux comparing with name: Linux
kmyfirewall: void KMFConfigDialog::slotSetOS( 0 )
kmyfirewall: Setting item: Linux
kmyfirewall: void KMFConfig::slotAutoConf() 
kmyfirewall: void KMFCheckListOutput::loadIcons()
kmyfirewall: void KMFCheckListOutput::clearList()
kmyfirewall: void KMFConfigDialog::slotEnableGentooMode( bool enable )
kmyfirewall: void KMFConfigDialog::slotSlackwareMode( bool enable )
kmyfirewall: void KMFCheckListOutput::appendLine(QString txt)
kmyfirewall: void KMFCheckListOutput::setStatus(bool ok,QString &err_msg)
kmyfirewall: void KMFCheckListOutput::appendLine(QString txt)
kmyfirewall: void KMFCheckListOutput::setStatus(bool ok,QString &err_msg)
kmyfirewall: void KMFCheckListOutput::appendLine(QString txt)
kmyfirewall: void KMFCheckListOutput::appendLine(QString txt)
kmyfirewall: void KMFCheckListOutput::setStatus(bool ok,QString &err_msg)
kmyfirewall: void KMFCheckListOutput::appendLine(QString txt)
kmyfirewall: void KMFCheckListOutput::appendLine(QString txt)
kmyfirewall: void KMFCheckListOutput::setStatus(bool ok,QString &err_msg)
kmyfirewall: void KMFCheckListOutput::appendLine(QString txt)
kmyfirewall: kmfdoc = new KMFIPTDoc(this,kmfdoc);
kmyfirewall: KMFDoc::KMFDoc( QObject *parent, const char *name ) : QObject( parent, name )
kmyfirewall: KMFGenericDoc::KMFGenericDoc( QObject *parent, const char *name ) : KMFDoc( parent, name )
kmyfirewall: void KMFGenericDoc::initDoc()
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: HTTP Register TCP Port:80
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: SSH Register TCP Port:22
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: SMB Register TCP Port:137
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: SMB Register TCP Port:138
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: SMB Register TCP Port:139
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: LDAP Register UDP Port:636
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: LDAP Register TCP Port:636
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: DNS Register UDP Port:53
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: SMTP Register TCP Port:25
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: POP3 Register TCP Port:110
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: POP3_SSL Register TCP Port:995
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: IMAP Register TCP Port:143
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: IMAP_SSL Register TCP Port:585
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: FTP Register TCP Port:21
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: Telnet Register TCP Port:23
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: NFS Register TCP Port:2049
kmyfirewall: void KMFProtocol::addPort( const QString& )
kmyfirewall: KMFProtocol: NFS Register UDP Port:2049
kmyfirewall: Found Library at:
kmyfirewall: INFORMATION: Creating file $KDEHOME/share/apps/kmyfirewall/protocols/kmfcustomprotocollibrary.xml
kmyfirewall: KDEHome dir: 
kmyfirewall: void KMFNetZone::setMaskLength( int len )
kmyfirewall: void KMFNetZone::setMaskLength( int len )
kmyfirewall: void KMFNetZone::setMaskLength( int len )
kmyfirewall: void KMFNetZone::setMaskLength( int len )
kmyfirewall: void KMFNetZone::setMaskLength( int len )
kmyfirewall: void KMFNetZone::setMaskLength( int len )
kmyfirewall: Doc address:0x8229a20
kmyfirewall: KMyFirewall::initStatusBar()
kmyfirewall: KMyFirewall::initMenu()
kmyfirewall: Init Actions...
kmyfirewall: KMyFirewall::initView()
kmyfirewall: void KMFGenericInterface::loadIcons()
kmyfirewall: void KMFGenericInterfa::loadIcons()
kmyfirewall: void KMFGenericInterfa::loadIcons()
kmyfirewall: void KMFGenericInterface::loadDoc( KMFGenericDoc* )
kmyfirewall: void KMFGenericInterfaceProtocol::loadDoc( KMFGenericDoc* doc )
kmyfirewall: void KMFGenericInterfaceProtocol::slotUpdateView()
kmyfirewall: Showing Incoming Zone
kmyfirewall: void KMFListViewItem::setupZoneView()
kmyfirewall: void KMFGenericInterfaceProtocol::slotUpdateView()
kmyfirewall: Showing Incoming Zone
kmyfirewall: void KMFListViewItem::setupZoneView()
kmyfirewall: void KMFGenericInterfaceHost::loadDoc( KMFGenericDoc* )
kmyfirewall: void KMFListViewItem::setupZoneView()
kmyfirewall: void KMFListViewItem::setupZoneView()
kmyfirewall: void KMFListViewItem::setupZoneView()
kmyfirewall: void KMFListViewItem::setupZoneView()
kmyfirewall: void KMFListViewItem::setupZoneView()
kmyfirewall: void KMFListViewItem::setupZoneView()
kmyfirewall: void KMFListViewItem::setupZoneView()
kmyfirewall: void KMFListViewItem::setupZoneView()
kmyfirewall: void KMFGenericInterfaceIcmp::loadDoc( KMFGenericDoc* )
kmyfirewall: void KMFGenericInterfaceNat::loadDoc( KMFGenericDoc* )
kmyfirewall: void KMFGenericInterfaceNat::slotUpdateView()
kmyfirewall: Setting Address Fields to: 0.0.0.0
kmyfirewall: void KMFGenericInterfaceNat::slotUpdateView()
kmyfirewall: Setting Address Fields to: 0.0.0.0
kmyfirewall: void KMFGenericInterfaceLogging::loadDoc( KMFGenericDoc* )
kmyfirewall: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file kmfgenericinterfaceparetui.rc
kmyfirewall: Found main API
kmyfirewall: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file kmfinstallerpluginui.rc
kmyfirewall: 

KMFInstallerPlugin: Finished Initialisation

 
kmyfirewall: Calling Constuctor: KMFCompilerInterface::KMFCompilerInterface()
kmyfirewall: Found main API
kmyfirewall: Found main API
kmyfirewall: Returning valid KMFGenericDoc pointer
kmyfirewall: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file kmfiptablescompiler.rc
kmyfirewall: KMFIPTablesCompiler: Finished initialisation.
kmyfirewall: void KMFGenericInterfacePart::slotEnableActions( bool )
kmyfirewall: void KMFConfigDialog::slotReceivedOutput(KProcess *, char *buffer, int buflen) 
kmyfirewall: Buffer: 
kmyfirewall: eth0
lo
kmyfirewall: 
kmyfirewall: Orig: eth0|lo|
kmyfirewall: Cut last Orig: eth0|lo
kmyfirewall: found | at 4
kmyfirewall: Orig: eth0|lo
kmyfirewall: void KMFCheckListOutput::appendLine(QString txt)
kmyfirewall: void KMFCheckListOutput::setStatus(bool ok,QString &err_msg)
kmyfirewall: Rest: lo
kmyfirewall: void KMFCheckListOutput::appendLine(QString txt)
kmyfirewall: void KMFCheckListOutput::setStatus(bool ok,QString &err_msg)
kmyfirewall: void KMFConfigDialog::slotProcessExited(KProcess*)

any help?

Also , a window appears and says :

¨ Warning - File Format change- Compatability Warning-As the file format used to save the rulesets has changed, rulesets created with KMyFirewall < 1.0beta1 WILL NOT work, don't even try it

---

### Post by oilchangeguy on 2007-09-15
why do you need this? ubuntu has it's own built in firewall, iptables.

---

### Post by fiskking on 2007-09-15
i was told to download it.. sorry  didnt know

---

### Post by fiskking on 2007-09-15
What about the  program ' Snort ´ then?

---

### Post by oilchangeguy on 2007-09-15
what's wrong with the built in firewall?

---

### Post by fiskking on 2007-09-15
well nothing I guess (use to Windows), read on a website where some ubuntu users downloaded Snort and kmyfirewall for their computer.  So the firewall here is pretty good?  I´m pretty new w/ this format so forgive my ignorance.

---

### Post by larry Gaminde on 2007-09-15
Download Firestarter its a GUI for iptables the built in firewall easy and you can watch the addresses of the people trying to access your system

---

