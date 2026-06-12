---
title: "Creative Zen Vision in Amark?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Hobo Joe on 2007-06-12
Ok, I'm having a bit of trouble with Amarok and a Zen Vision. I set it up as an MTP device, and it see's all the music on there, but when I click on it to play it or to copy it to collection, it doesn't work.
In the music view, it shows up all the artists and the albums and songs, but when I add them to the playlist, it says 'error: could not open [filename].mp3', and the song names all say 'from', and all the other colums are blank.

Any help would be greatly appreciated.

---

### Post by Hobo Joe on 2007-06-12
Can't anyone help?

I tried Gnomad2, and it worked, but it transfers the music in individual files, and not it their respective folders like they should be, not to mention that the program has a horrible interface.

---

### Post by Hobo Joe on 2007-06-14
I re-installed a couple files and now the command 'mtp-detect' gives this:

```

Autodetected device "Creative Zen Vision:M" (VID=041e,PID=413e) is known.
PTP: Opening session
Connected to MTP device.
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 413e
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Device flags: 0x00000000
Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative Zen Vision:M
   Device version: 1.40.02_0.00.22
   Serial number: 00023C026E02105A9CCC480DBFF51AD4
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0;microsoft.com/WMPPD: 10.0;microsoft.com/WMDRMPD: 10.1;audible.com: 1.0;
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1007: Get object handles
   100c: Send object info
   100d: Send object
   100f: Format storage
   1014: Get device property description
   1015: Get device property value
   1006: Get number of objects
   1008: Get object info
   1009: Get object
   100b: Delete object
   1010: Reset device
   1016: Set device property value
   1017: Reset device property value
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9808: Send object property list
   9807: Get interdependent property description
   9810: Get object references
   9811: Set object references
   9201: Report Added/Deleted Items
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
Events supported:
   None.
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Device Friendly Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd201: Unknown property
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
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc91: UseCount
      dc8a: Rating
      d901: BuyFlag
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   b901: WMA
      de99: AudioWAVECodec
      de9a: AudioBitRate
      dc46: Artist
      dc89: Duration
      dc8b: Track
      dc8c: Genre
      dc99: OriginalReleaseDate
      dc9a: AlbumName
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc91: UseCount
      dc8a: Rating
      d901: BuyFlag
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   3008: MS Wave
      dc46: Artist
      dc89: Duration
      dc8b: Track
      dc8c: Genre
      dc99: OriginalReleaseDate
      dc9a: AlbumName
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc91: UseCount
      dc8a: Rating
      d901: BuyFlag
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   b904: Audible.com Codec
      da01: unknown(da01)
      da02: unknown(da02)
      da03: unknown(da03)
      dc46: Artist
      dc89: Duration
      dc8b: Track
      dc8c: Genre
      dc99: OriginalReleaseDate
      dc9a: AlbumName
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc91: UseCount
      dc8a: Rating
      d901: BuyFlag
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   ba05: Abstract Audio Video Playlist
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   ba01: Abstract Multimedia Album
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   ba03: Abstract Audio Album
      dc86: RepresentativeSampleData
      dc81: RepresentativeSampleFormat
      dc83: RepresentativeSampleHeight
      dc82: RepresentativeSampleSize
      dc84: RepresentativeSampleWidth
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   3801: JPEG
      dc88: Height
      dc86: RepresentativeSampleData
      dc81: RepresentativeSampleFormat
      dc83: RepresentativeSampleHeight
      dc82: RepresentativeSampleSize
      dc84: RepresentativeSampleWidth
      dc87: Width
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   300a: MS AVI
      de99: AudioWAVECodec
      de9a: AudioBitRate
      de9d: FramesPerThousandSeconds
      dc88: Height
      de91: TotalBitRate
      de9b: VideoFourCCCodec
      de9c: VideoBitRate
      dc87: Width
      dc86: RepresentativeSampleData
      dc81: RepresentativeSampleFormat
      dc83: RepresentativeSampleHeight
      dc82: RepresentativeSampleSize
      dc84: RepresentativeSampleWidth
      dc89: Duration
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   300c: ASF
      de99: AudioWAVECodec
      de9a: AudioBitRate
      de9d: FramesPerThousandSeconds
      dc88: Height
      de91: TotalBitRate
      de9b: VideoFourCCCodec
      de9c: VideoBitRate
      dc87: Width
      dc86: RepresentativeSampleData
      dc81: RepresentativeSampleFormat
      dc83: RepresentativeSampleHeight
      dc82: RepresentativeSampleSize
      dc84: RepresentativeSampleWidth
      dc89: Duration
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   b982: MP4
      de99: AudioWAVECodec
      de9a: AudioBitRate
      de9d: FramesPerThousandSeconds
      dc88: Height
      de91: TotalBitRate
      de9b: VideoFourCCCodec
      de9c: VideoBitRate
      dc87: Width
      dc86: RepresentativeSampleData
      dc81: RepresentativeSampleFormat
      dc83: RepresentativeSampleHeight
      dc82: RepresentativeSampleSize
      dc84: RepresentativeSampleWidth
      dc89: Duration
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   300b: MPEG
      de99: AudioWAVECodec
      de9a: AudioBitRate
      de9d: FramesPerThousandSeconds
      dc88: Height
      de91: TotalBitRate
      de9b: VideoFourCCCodec
      de9c: VideoBitRate
      dc87: Width
      dc86: RepresentativeSampleData
      dc81: RepresentativeSampleFormat
      dc83: RepresentativeSampleHeight
      dc82: RepresentativeSampleSize
      dc84: RepresentativeSampleWidth
      dc89: Duration
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   b981: WMV
      de99: AudioWAVECodec
      de9a: AudioBitRate
      de9d: FramesPerThousandSeconds
      dc88: Height
      de91: TotalBitRate
      de9b: VideoFourCCCodec
      de9c: VideoBitRate
      dc87: Width
      dc86: RepresentativeSampleData
      dc81: RepresentativeSampleFormat
      dc83: RepresentativeSampleHeight
      dc82: RepresentativeSampleSize
      dc84: RepresentativeSampleWidth
      dc89: Duration
      de93: SampleRate
      de94: NumberOfChannels
      de95: AudioBitDepth
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   bb83: vCard3
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   be03: vCalendar2
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   3000: Undefined Type
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   3001: Association/Directory
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
   b802: Firmware
      dc01: StorageID
      dc0b: ParentObject
      dc02: ObjectFormat
      dc04: ObjectSize
      dc07: ObjectFileName
      dc41: PersistantUniqueObjectIdentifier
      dc4f: NonConsumable
      dc44: Name
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 29952966656
      FreeSpaceInBytes: 21042102272
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: 00023C026E02105A9CCC480DBFF51AD4
Special directories:
   Default music folder: 0x00000084
   Default playlist folder: 0x0000005c
   Default picture folder: 0x00000068
   Default video folder: 0x0000006c
   Default organizer folder: 0x00000064
   Default zencast folder: 0x00000074
   Default album folder: 0x00000000
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: My Zen
   Synchronization partner: (NULL)
   Battery level 255 of 255 (100%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   Audible.com Audio Codec
   JPEG file
   Audio Video Interleave
   Microsoft Advanced Systems Format
   MPEG-4 Part 14 Container Format (Audio+Video Empahsis)
   MPEG video stream
   Microsoft Windows Media Video
   VCard version 3
   VCalendar version 2
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20050523 07:31:32Z#</VALUE><FLAG>DRM_CLK_NOT_SET</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">AjwCAFoQAm4NSMyc1Br1vwAAAAA=</UNIQUEID><PUBLICKEY private="1">nim6628T1McnjJvIwZYSvzotWk1RBZhKOA764TXKrCBQN1nP7dQ9Sg==</PUBLICKEY><KEYDATA>as6z09UFWyBY6spQG3uOMzofSqA=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>7QX511MOyK2P/LkH4SQNlWQAxAJP8hmAT6AY+GMS/m6VQA6zHeHpdA==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>KiEexyN4YBThLxIKdRnNNo5QNYI=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.103.61</SECURITYVERSION><CERTIFICATE private="1">nim6628T1McnjJvIwZYSvzotWk1RBZhKOA764TXKrCBQN1nP7dQ9SgIEZz1Ze3OmsjE36SqQg/FKTYNDI1rsEYEC9RQ7/yeL1l1xn0v8hGAqqnRd</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>Creative Zen Vision:M</NAME>
  <MANUFACTURER>CL Direct Pte Ltd.</MANUFACTURER>
  <MODEL>DVP-HD0003</MODEL>
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
  </LIMITS><PUBLICKEY>Zyqn8gWDO+E0O5uFWAITnXpHrzfRKPtanLWS4c0CWBv4HVL8VMm0QQ==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>g27HSbQgG+GZO2dlcOK0qdK/Ql+5HU7kWCXnqSDDHko5fruJpT/pVQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>673</AUTH_ID><PUBLICKEY>apoWlp0LevRxXWHcSskvn/VSsG5YjXoM7Bya7bMdc0GO3VM9fxhIgw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>MJmLft7Asiwh9iDeM/VogDjM4G5U6x0E1Vws11mQN0yJjBMkGWRZVQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>dhVs0/oSDCgWs5g9yvEdkRatr1eLsaMe7Kws0MwaOWWebmtq1TZABQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>
PTP: Closing session
OK.

```

Before it just said 'Creative Zen Vision:M device autodetected'.

But I'm still having the same problem in Amarok.

I tried kzenexplorer too, and it says 'no jukebox detected'


....Anyone?  I'd easily settle for just the simple ability to browse through the files, at this point I don't even really care if I can't use it in Amarok.

---

