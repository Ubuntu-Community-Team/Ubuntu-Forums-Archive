---
title: "Help with portable media player"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Dark_Man on 2008-01-08
Hello all. New user here. I am running Ubuntu 6.10. I have a Creative Zen Sleek Photo mp3 player. When I  plug the device in the system sees it as a camera for some reason. I have both Amarok and Gnomad2 installed and neither one will recognize it. Went into the configuration for amarok but there is no option for mtp device. I ran **mtp-detect** and got this output. Any help is appreciated. Thanks

darkman@Leviathan:~$ mtp-detect
Autodetected device "Creative Zen Sleek Photo" (VID=041e,PID=413d) is known.
PTP: Opening session
Connected to MTP device.
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 413d
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Device flags: 0x00000000
Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative Zen Sleek Photo
   Device version: 1.10.01_0.00.06
   Serial number: 01012551C9039094804A1E1BC9039094
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0;microsoft.com/WMPPD: 10.0;microsoft.com/WMDRMPD: 10.1;
Supported operations:
   0x1001
   0x1002
   0x1003
   0x1004
   0x1005
   0x1007
   0x100c
   0x100d
   0x100f
   0x1014
   0x1015
   0x1006
   0x1008
   0x1009
   0x100b
   0x1010
   0x1016
   0x1017
   0x9801
   0x9802
   0x9803
   0x9804
   0x9805
   0x9806
   0x9808
   0x9807
   0x9810
   0x9811
   0x9201
   0x9101
   0x9102
   0x9103
   0x9104
   0x9105
   0x9106
   0x9107
   0x9108
   0x9109
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
      de99: AudioWAVECodec
      de9a: AudioBitRate
      dc46: Artist
      dc89: Duration
      dc8b: Track
      dc8c: Genre
      dc99: OriginalReleaseDate
      dc9a: AlbumName
      dc44: Name
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc91: UseCount
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
   b901: WMA
      de99: AudioWAVECodec
      de9a: AudioBitRate
      dc46: Artist
      dc89: Duration
      dc8b: Track
      dc8c: Genre
      dc99: OriginalReleaseDate
      dc9a: AlbumName
      dc44: Name
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc91: UseCount
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
   3008: MS Wave
      dc46: Artist
      dc89: Duration
      dc8b: Track
      dc8c: Genre
      dc99: OriginalReleaseDate
      dc9a: AlbumName
      dc44: Name
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc91: UseCount
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
   ba05: Abstract Audio Video Playlist
      dc44: Name
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
   3801: JPEG
      dc88: Height
      dc04: ObjectSize
      dc86: RepresentativeSampleData
      dc81: RepresentativeSampleFormat
      dc83: RepresentativeSampleHeight
      dc82: RepresentativeSampleSize
      dc84: RepresentativeSampleWidth
      dc87: Width
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
   bb83: vCard3
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
   be03: vCalendar2
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
   3000: Undefined Type
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
   3001: Association/Directory
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
   b802: Firmware
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
Special directories:
   Default music folder: 0x0000cff4
   Default playlist folder: 0x0000006b
   Default picture folder: 0x00000077
   Default video folder: 0x00000000
   Default organizer folder: 0x00000073
   Default zencast folder: 0x00000000
MTP-specific device properties:
   Friendly name: Dark Man
   Synchronization partner: {6D7C7031-D314-49EC-A78F-824B29282891}
   Total bytes on device: 19978944512 (19053 MB)
   Free bytes on device: 18106466304 (17267 MB)
   Storage description: "Storage Media"
   Volume label: "01012551C9039094804A1E1BC9039094"
   Battery level 221 of 255 (86%)
libmtp supported (playable) filetypes:
   ISO MPEG Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   JPEG file
   VCard version 3
   VCalendar version 2

Secure Time:
<DRMCLOCK type="status"><VALUE>#20080108 07:03:58Z#</VALUE><FLAG>DRM_CLK_SET</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">AQElUckDkJSASh4byQOQlAAAAAA=</UNIQUEID><PUBLICKEY private="1">wxesstMnV4NzqRgxTZf3gbb+VWldPLAKWRNjlsivLLeyZQdDOJ1wXQ==</PUBLICKEY><KEYDATA>NsJWL4pMyCb/6qy+c7XQ+lPdKWw=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>QdG7m0YDhuAKKIU07FGzAdA9hkoJ+tR9o+R5fM752gB7gwGbSr3/iA==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>UFmZtOijx0RvWmkIDP+OHEYjzRk=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.102.251</SECURITYVERSION><CERTIFICATE private="1">wxesstMnV4NzqRgxTZf3gbb+VWldPLAKWRNjlsivLLeyZQdDOJ1wXQIEZvv8fT4xCoyvjyyyf34w5PyyNs2oCopz7RyR4UJ0HWS5m7z86OMkTORP</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>Creative Zen Sleek Photo</NAME>
  <MANUFACTURER>CL Direct Pte Ltd.</MANUFACTURER>
  <MODEL>DAP-HD0019</MODEL>
  <SECURITYLEVEL>2000</SECURITYLEVEL>
  <HARDWARE_VER_MAJOR>1</HARDWARE_VER_MAJOR>
  <HARDWARE_VER_MINOR>0</HARDWARE_VER_MINOR>
  <FIRMWARE_VER_MAJOR>1</FIRMWARE_VER_MAJOR>
  <FIRMWARE_VER_MINOR>0</FIRMWARE_VER_MINOR>
  <FEATURES>
    <CLOCK>2</CLOCK>
    <SECURECLOCK>
      <URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL>
      <PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY>
    </SECURECLOCK>
    <METERING>1</METERING>
    <LICENSE_ACQ>0</LICENSE_ACQ>
    <LICENSE_SYNC>1</LICENSE_SYNC>
    <ENCRYPTION>0</ENCRYPTION>
    <SYMMETRIC_OPT>1</SYMMETRIC_OPT>
  </FEATURES>
  <LIMITS>
    <MAXCHAINDEPTH>2</MAXCHAINDEPTH>
    <MAXLICENSESIZE>10240</MAXLICENSESIZE>
    <MAXHEADERSIZE>5120</MAXHEADERSIZE>
  </LIMITS><PUBLICKEY>1g4IeC/PVU+rsBUUCYU9qgysd2wtM39JdZMI4baJctJWXIBjC/X2fw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>2aq1nOVsmyl4TlkG9jB2BzZk3kQof44kn5ga6Fw0E2QlwRJzy/SEBw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>607</AUTH_ID><PUBLICKEY>f8GmLC8Ps6YG622nfN2uZOG09Aw/NVJjw9EkQ8+3zhUA4w+wT6soDQ==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>D1NfueBCHqD760o4Aj+5Ww81g1nRrGfYM2Eg/5v+2LXhYF6LVJLGEA==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>il+pFePnSDV910S+GJtfK2h8SzC/cvu6AmJV0vMOc1qbhEycGFsjfw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>

Device description WMPInfo.xml file:
<DeviceInfo>
    <WMP DeviceID="{BEDE104C-1A24-48D6-890D-9AF21179A787}" RelationshipID="{6D7C7031-D314-49EC-A78F-824B29282891}"/>
</DeviceInfo>

PTP: Closing session
OK.

---

### Post by Dark_Man on 2008-01-08
Fixed. I upgraded to feisty and now it works

---

