---
title: "mtp device not recognized"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by discoade on 2007-12-21
hi guys

ubuntu isnt recognizing my mtp mp3 player. its a samsung yp k3.
i had to do a reinstall of ubuntu and it worked before that.
I have amarok and rhythembox but neither recognize it and it dosnt appear on the desktop as it used to!

Any ideas?

---

### Post by hyper_ch on 2007-12-21
Is it a usb device? (Well, I guess so but not sure).

If so, run this command and post the output:

```

lsusb

```

---

### Post by jordanmthomas on 2007-12-21
I don't use Ubuntu, so I don't know if this is installed by default, but do you have the mtp libraries installed?
```
sudo apt-get install libmtp6
```

---

### Post by discoade on 2007-12-21
adrian@adrian-desktop:~$ lsusb
Bus 005 Device 010: ID 04e8:5081 Samsung Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
adrian@adrian-desktop:~$ 

the latest mtp library is installed

---

### Post by discoade on 2007-12-21
adrian@adrian-desktop:~$ sudo apt-get install libmtp6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmtp6 is already the newest version.
The following packages were automatically installed and are no longer required:
  mplayer-skins libsvga1 python-qt3 libggi2 python-sip4 libgii1
  libgii1-target-x libdvdnav4 libungif4g
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
adrian@adrian-desktop:~$

---

### Post by hyper_ch on 2007-12-21
> **discoade said:**
> Bus 005 Device 010: ID 04e8:5081 Samsung Electronics Co., Ltd

Well, good news is, it's being recognized... bad news is I have no clue why it's not working.

---

### Post by discoade on 2007-12-21
:) ditto
ive got it working sort of in rythembox i had to enable it in a menu but its next to useless as you cant write to the device only read! what's the point of that! ive already got all the mp3s on my hdd! :)

Amorok worked a treat last install shows all the play lists everything!  :(

---

### Post by Wilfred on 2007-12-21
Hi,

I use gnomad2 (installed via add/remove programs or synaptic) to update my mpt device (Creative Zen M:)

It may not be the most userfriendly piece of software, it does the job quite nice

---

### Post by lamalex on 2007-12-21
I use MTPFS, so I can just drag and drop files like an external hard drive. Works well for me.

---

### Post by lamalex on 2007-12-21
Do you have mtp-tools installed? Install them too and see if you can get at it. mtp-detect is a good command, you can also do command line transfers with mtp-tools, very handy indeed.

---

### Post by discoade on 2007-12-21
Tried gnomad2 it says no jukeboxes detected.

cant find mtpfs in the repos.

installed mtp-tools! What do i do with it? :confused:

---

### Post by discoade on 2007-12-21
typed mtp-detect in to terminal and got this!

adrian@adrian-desktop:~$ mtp-detect
libmtp version: 0.2.1

Attempting to connect device(s)
PTP: Opening session
PTP: request code 0x1002 sending req wrote only 0 bytes instead of 16
PTP_ERROR_IO: Trying again after resetting USB
inep: usb_get_endpoint_status(): Connection timed out
outep: usb_get_endpoint_status(): Connection timed out
usb_clear_halt() on IN endpoint: Connection timed out
usb_clear_halt() on OUT endpoint: Connection timed out
usb_clear_halt() on INTERRUPT endpoint: Connection timed out
PTP: Opening session
Detect: Successfully connected 1 devices
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 04e8
   idProduct: 5081
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Device flags: 0x00000000
Microsoft device descriptor 0xee:
        0000: 1203 4d00 5300 4600 5400 3100 3000 3000   ..M.S.F.T.1.0.0.
        0010: 0100                                      ..
Device info:
   Manufacturer: Samsung Inc.
   Model: Samsung YP-K3
   Device version: VER 3.05 WA JN
   Serial number: 2B391FB20014592288C0218BF0003F16
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com/WMDRMPD: 10.1;audible.com: 1.0;
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1006: Get number of objects
   1007: Get object handles
   1008: Get object info
   1009: Get object
   100b: Delete object
   100c: Send object info
   100d: Send object
   100f: Format storage
   1010: Reset device
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   1017: Reset device property value
   9810: Get object references
   9811: Set object references
   9802: Get object property description
   9801: Get object properties supported
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   101b: Get partial object
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
   910a: Send WMDRM-PD Command
   910b: Send WMDRM-PD Request
Events supported:
   None.
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Device Friendly Name
   0xd101: Secure Time
   0xd102: Device Certificate
Playable File (Object) Types and Object Properties Supported:
   3009: MP3
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      dc9a: AlbumName STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
   b901: WMA
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
      de93: SampleRate UINT32 data type range: MIN 8000, MAX 48000, STEP 50 READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      dc9a: AlbumName STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 0, 1, 2, 3, 8, 9, 11, 49, 50, 80, 85, 352, 353, 354, 355, 356, 41222,  GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
   3801: JPEG
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
   3001: Association/Directory
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
   ba05: Abstract Audio Video Playlist
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
   3000: Undefined Type
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
   b802: Firmware
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
   ba03: Abstract Audio Album
      dc97: EffectiveRating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc8a: Rating UINT16 data type range: MIN 0, MAX 100, STEP 1 GET/SET
      dc44: Name STRING data type GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc09: DateModified STRING data type GET/SET
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc46: Artist STRING data type GET/SET
      dc8c: Genre STRING data type GET/SET
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 4037017600
      FreeSpaceInBytes: 567652352
      FreeSpaceInObjects: 16730
      StorageDescription: Internal Storage
      VolumeIdentifier: 2B391FB20014592288C0218BF0003F16
Special directories:
   Default music folder: 0x20000003
   Default playlist folder: 0x20000005
   Default picture folder: 0x20000004
   Default video folder: 0x00000000
   Default organizer folder: 0x00000000
   Default zencast folder: 0x00000000
   Default album folder: 0x00000000
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: Samsung YP-K3
   Synchronization partner: Longhorn Sync Engine
   Battery level 100 of 100 (100%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   JPEG file
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20060322 15:21:15Z#</VALUE><FLAG>DRM_CLK_NEEDS_REFRESH</FLAG></DRMCLOCK>AG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">KzkfsgAUWSKIwCGL8AA/FgAAAAA=</UNIQUEID><PUBLICKEY private="1">I5QxOMp3YfbF8lBTFZ6SnDp/eQ4L3qa7rE/SqdBCY6G/bkM3mk79Bg==</PUBLICKEY><KEYDATA>CEvkbNzcKVp09nG1MtBeOjWmZb0=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>+cc/g4nVeCx1p3wqM7B4dQWH2HReVwAh+uBvOBgojRQa9wHLE4j8Rg==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>a56QeaE9Xg9BU3XOqo7UD9YTuHI=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.105.107</SECURITYVERSION><CERTIFICATE private="1">I5QxOMp3YfbF8lBTFZ6SnDp/eQ4L3qa7rE/SqdBCY6G/bkM3mk79BgIEaWuth4BSk1cE7/55Y81tpExyAQuyU+nSY4BToGbh530H+lUf75Xaty90</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>TCCSDKBoard</NAME><MANUFACTURER>Telechips</MANUFACTURER><MAKE>Telechips</MAKE><DISTRIBUTOR>WideWorldImporters</DISTRIBUTOR><MODEL>TCC7XX</MODEL><SECURITYLEVEL>2000</SECURITYLEVEL><HARDWARE_VER_MAJOR>1</HARDWARE_VER_MAJOR><HARDWARE_VER_MINOR>0</HARDWARE_VER_MINOR><FIRMWARE_VER_MAJOR>1</FIRMWARE_VER_MAJOR><FIRMWARE_VER_MINOR>0</FIRMWARE_VER_MINOR><FEATURES><CLOCK>2</CLOCK><SECURECLOCK><URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL><PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY></SECURECLOCK><METERING>1</METERING><LICENSE_ACQ>0</LICENSE_ACQ><LICENSE_SYNC>1</LICENSE_SYNC><ENCRYPTION>0</ENCRYPTION><SYMMETRIC_OPT>1</SYMMETRIC_OPT></FEATURES><LIMITS><MAXCHAINDEPTH>2</MAXCHAINDEPTH><MAXLICENSESIZE>10240</MAXLICENSESIZE><MAXHEADERSIZE>5120</MAXHEADERSIZE></LIMITS><PUBLICKEY>qOxIhjTiT16ThbPhUSr8owa0VUkPuULltIn1cK3WdQYpQoZn2vJgYQ==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>3biCcFMgsYuHBQvlL3qw5DhmNjwQk60qmziGE7Oaf/6O9YEap6+/Bg==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>1231</AUTH_ID><PUBLICKEY>uVjt9gtU10r8MkVOz6naLCacO3grl8HqKs4gN5R73dJBaF7nKmTIHA==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>3k5byRIQtCXmA6y0BJO1qA7Xmx9/+yMnCaukIoVpqO95vefmrE9DLQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>rjswZ823zQz7gHDqqLTEbryN+F0NpPVMYU3VecFmAJMY+TgwiexHAA==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>
WMPInfo.xml Does not exist on this device
PTP: Closing session
inep: usb_get_endpoint_status(): Connection timed out
outep: usb_get_endpoint_status(): Connection timed out
usb_clear_halt() on IN endpoint: Connection timed out
usb_clear_halt() on OUT endpoint: Connection timed out
usb_clear_halt() on INTERRUPT endpoint: Connection timed out
OK.
adrian@adrian-desktop:~$ 

????:confused:

---

### Post by discoade on 2007-12-22
bump

---

### Post by kaniza on 2008-03-04
I'm having difficulty with my Zen M being recognized as well.

My system is up to date with all of the MTP tools and Gnomad (and Amarok as well), but it's not recognizing the player itself.

I do MTP-Detect and get no results. For some reason, my computer will recognize the player enough to charge it, but lsusb also comes up with new results.

I've gone through every remotely related topic in these forums and elsewhere. Gnomad2 *used* to work on my system, but I've been syncing it with files on my computer at work (Win XP) recently. Dunno how or if that's the cause of the problem, but I welcome all suggestions!

---

### Post by joxenford on 2008-03-04
I also have a problem with gnomad2 and the "...no jukebox found" error.  I'm running libmtp 0.2.1
and when I run mtp-detect it does connect to Creative Zen Vison M (60GB)   This is one of the last things I need to get working in Ubuntu to help make this switch permanent.  

I've been through the boards and nothing has worked.

Thanks in advance for any help.

---

