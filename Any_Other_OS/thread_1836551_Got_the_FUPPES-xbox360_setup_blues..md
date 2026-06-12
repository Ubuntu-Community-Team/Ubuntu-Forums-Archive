---
title: "Got the FUPPES-xbox360 setup blues."
date: 2011-08-31
forum: Any Other OS
---

### Post by LookingDownTheCross on 2011-08-31
Well after a rigorous time installing FUPPES, I finally got the correct latest, stable release installed, and it will actually run, and get recognized by the xbox, but none of the media will show up, I've checked my fuppes.cfg & vfolder.cfg  with several from different sources from across the interwebz(been trying to setup streaming to my 360 for 3 days), and still no dice.
Can anybody here help me with something specific maybe?

Also I'm completely busting my linux cherry right now, installed Linux Mint 11 on friday.
Acer-Aspire 5742-7120

and the 360 is one of the newer "S" models. 4GB model, no hdd.


fuppes.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
<shared_objects>
<dir>/home/username/Music</dir>
<dir>/home/username/Videos</dir>
</shared_objects>

<network>
<interface>eth1</interface>
<http_port>1080</http_port>
<allowed_ips>
<!--<ip>192.168.254.254</ip>-->
<!--<ip>192.168.0.***</ip>-->
<!--<ip>192.168.0.***</ip>-->
</allowed_ips>
</network>
<content_directory>
<!--a list of possible charsets can be found under:
http://www.gnu.org/software/libiconv/-->
<local_charset>UTF-8</local_charset>
<!--libs used for metadata extraction when building the database. [true|false]-->
<use_imagemagick>true</use_imagemagick>
<use_taglib>true</use_taglib>
<use_libavformat>true</use_libavformat>
</content_directory>
<transcoding>
<!--[lame|twolame]-->
<audio_encoder>lame</audio_encoder>
<!--[true|false]-->
<transcode_vorbis>true</transcode_vorbis>
<transcode_musepack>true</transcode_musepack>
<transcode_flac>true</transcode_flac>
</transcoding>
<device_settings>
<!--"default" settings are inhertied by specific devices and can be overwritten-->
<device name="default">
<!--specify the maximum length for file names (0 or empty = unlimited)-->
<max_file_name_length>0</max_file_name_length>
<!--[file|container]-->
<playlist_style>file</playlist_style>
<show_childcount_in_title>false</show_childcount_in_title>
<enable_dlna>true</enable_dlna>
<transcoding_release_delay>4</transcoding_release_delay>
<file_settings>
<!--audio files-->
<file ext="mp3">
<type>AUDIO_ITEM</type>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
</file>
<file ext="ogg">
<type>AUDIO_ITEM</type>
<mime_type>application/octet-stream</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>vorbis</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="mpc">
<type>AUDIO_ITEM</type>
<mime_type>application/octet-stream</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>musepack</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="wav">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-wav</mime_type>
</file>
<file ext="flac">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-flac</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>flac</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="wma">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-ms-wma</mime_type>
<dlna>WMAFULL</dlna>
</file>
<!--image files-->
<file ext="jpg">
<ext>jpeg</ext>
<type>IMAGE_ITEM</type>
<mime_type>image/jpeg</mime_type>
<convert enabled="false">
<!--<dcraw enabled="true">-q 0</dcraw>-->
<ext>png</ext>
<mime_type>image/png</mime_type>
<height>0</height>
<width>0</width>
<!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
<greater>false</greater>
<!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
<less>false</less>
<!--set "less" and "greater" to "false" if you always want to resize-->
</convert>
</file>
<file ext="bmp">
<type>IMAGE_ITEM</type>
<mime_type>image/bmp</mime_type>
</file>
<file ext="png">
<type>IMAGE_ITEM</type>
<mime_type>image/png</mime_type>
</file>
<file ext="gif">
<type>IMAGE_ITEM</type>
<mime_type>image/gif</mime_type>
</file>
<!--video files-->
<file ext="mpg">
<ext>mpeg</ext>
<type>VIDEO_ITEM</type>
<mime_type>video/mpeg</mime_type>
</file>
<file ext="mp4">
<type>VIDEO_ITEM</type>
<mime_type>video/mp4</mime_type>
</file>
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/avi</mime_type>
</file>
<file ext="wmv">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-wmv</mime_type>
</file>
<file ext="vob">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-vob</mime_type>
</file>
<file ext="vdr">
<type>VIDEO_ITEM</type>
<mime_type>video/x-extension-vdr</mime_type>
<transcode enabled="true">
<ext>vob</ext>
<mime_type>video/x-ms-vob</mime_type>
</transcode>
</file>
<file ext="flv">
<type>VIDEO_ITEM</type>
<mime_type>application/x-flash-video</mime_type>
</file>
<file ext="asf">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-asf</mime_type>
</file>
<!--playlists-->
<file ext="pls">
<type>PLAYLIST</type>
<mime_type>audio/x-scpls</mime_type>
</file>
<file ext="m3u">
<type>PLAYLIST</type>
<mime_type>audio/x-mpegurl</mime_type>
</file>
</file_settings>
</device>
<!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
<device name="PS3" enabled="false">
<user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
<user_agent>PLAYSTATION3</user_agent>
<!--<ip></ip>-->
<enable_dlna>true</enable_dlna>
<transcoding_release_delay>50</transcoding_release_delay>
<file_settings>
<file ext="ogg">
<type>AUDIO_ITEM_MUSIC_TRACK</type>
<transcode enabled="true">
<http_encoding>stream</http_encoding>
</transcode>
</file>
</file_settings>
</device>
<device name="Xbox 360" virtual="Xbox 360" enabled="true">
<user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
<user_agent>Xenon</user_agent>
<xbox360>true</xbox360>
<file_settings>
<file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
<file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
<file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>
</file_settings>
<description_values>
<friendly_name>LM: Media</friendly_name>
<model_name>Windows Media Connect compatible (%s)</model_name>
<model_number>2.0</model_number>
</description_values>
</device>
<device name="Telegent TG 100" virtual="default" enabled="false">
<user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
<user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
<playlist_style>file</playlist_style>
<max_file_name_length>101</max_file_name_length>
</device>
</device_settings>
</fuppes_config>
```vfolder.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

<vfolder_layout device="default" enabled="false">

<vfolder name="Genre">
<vfolders property="genre">
<items type="audioItem" />
</vfolders>
</vfolder>

<vfolder name="Genre/Artists">
<vfolders property="genre">
<vfolders property="artist">
<items type="audioItem" />
</vfolders>
</vfolders>
</vfolder>

<vfolder name="Artists/Albums">
<vfolders property="artist">
<vfolders property="album">
<items type="audioItem" />
</vfolders>
</vfolders>
</vfolder>

<vfolder name="ABC/Artists/Albums">
<vfolders split="ABC">
<vfolders property="artist">
<vfolders property="album">
<items type="audioItem" />
</vfolders>
</vfolders>
</vfolders>
</vfolder>

<vfolder name="Photos">
<vfolder name="All">
<items type="imageItem" />
</vfolder>
<vfolder name="Folders">
<folders filter="contains(imageItem)" />
</vfolder>
</vfolder>

<vfolder name="Videos">
<vfolder name="All">
<items type="videoItem" />
</vfolder>
<vfolder name="Folders">
<folders filter="contains(videoItem)" />
</vfolder>
</vfolder>

<vfolder name="shared dirs">
<shared_dirs full_extend="true" />
</vfolder>

</vfolder_layout>

<vfolder_layout device="Xbox 360" enabled="true">
<vfolder name="Video" id="2">
<vfolder name="Folders" id="21">
<folders filter="contains(videoItem)" />
</vfolder>
</vfolder>
</vfolder_layout>
</fuppes_vfolder_config>


```as a sidenote, I have tried XBMC, as well as ushare, same thing happened with them. (connect to xbox, but no files or folders)

---

### Post by Perfect Storm on 2011-09-01
Moved to Other OS/Distro Talk.

Please note that for support of Linux Mint, you'll find here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by sffvba[e0rt on 2011-09-01
For what it is worth, make sure your media is in a format that the Xbox can play back (test your avi's on a USB)...  Not sure that is your issue but it could be...


404

---

### Post by blither on 2011-09-03
I had the same issue a while back when I first got my 360 and wanted to use my Ubuntu server.

First, I would like to mention that I do not use any other devices for streaming besides my 360, so this script will probably alter what you expect to show up if you use other streaming devices.

Second, this still requires the rebuild or update to be run to get new files to show up.  Although, inotify could be setup to automatically do this; I will not discuss this.

Third, if you are satisfied with all of the files showing up in a default base folder view you do not need to run the sql script.  If you would like your files to show up as they do on your disk then you should execute the following command with the sql script provided.  I should also note that this script hasn't been vigorously tested on other systems, I have just been using it for me and it seems to work.

Forth, if I remember correctly you shouldn't have to download the media package from Xbox Live until you attempt to play an AVI file.

Before executing sql script below...
```
/Movies
  --/Movie 1
/tv
 --/Show 1
/Show 1
 --/Series 1
/Series 1
 --/Episode 1
...
```

After executing sql script below...
```
/Movies
 --/Movie 1
/tv
 --/Show 1
   --/Series 1
     --/Episode 1
```



You should not execute this next line until you have run the rebuild/update from the web or command.
```
cat fuppes_xbox.sql | sqlite3 fuppes.db
```

Well here it goes.

Cheers, and I hope this helps.

```
blither@localhost:~$ fuppes --help
            FUPPES - 0.655
    the Free UPnP Entertainment Service
      http://fuppes.ulrich-voelkel.de
```

fuppes.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
 <shared_objects>
   <dir>/dir/to/media</dir>
 </shared_objects>

<network>
   <interface>eth0</interface>
   <http_port>12345</http_port>
   <allowed_ips>
   </allowed_ips>
 </network>
 <content_directory>
   <local_charset>UTF-8</local_charset>
   <use_imagemagick>true</use_imagemagick>
   <use_taglib>true</use_taglib>
   <use_libavformat>true</use_libavformat>
 </content_directory>
 <transcoding>
   <audio_encoder>lame</audio_encoder>
   <transcode_vorbis>true</transcode_vorbis>
   <transcode_musepack>true</transcode_musepack>
   <transcode_flac>true</transcode_flac>
 </transcoding>
 <device_settings>
   <device name="default">
     <max_file_name_length>0</max_file_name_length>
     <playlist_style>file</playlist_style>
     <show_childcount_in_title>false</show_childcount_in_title>
     <enable_dlna>false</enable_dlna>
     <transcoding_release_delay>4</transcoding_release_delay>
     <file_settings>
       <file ext="mp3">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/mpeg</mime_type>
         <dlna>MP3</dlna>
       </file>
       <file ext="ogg">
         <type>AUDIO_ITEM</type>
         <mime_type>application/octet-stream</mime_type>
         <transcode enabled="true">
           <ext>mp3</ext>
           <mime_type>audio/mpeg</mime_type>
           <dlna>MP3</dlna>
           <http_encoding>chunked</http_encoding>
           <decoder>vorbis</decoder>
           <encoder>lame</encoder>
           <bitrate>192</bitrate>
           <samplerate>44100</samplerate>
         </transcode>
       </file>
       <file ext="mpc">
         <type>AUDIO_ITEM</type>
         <mime_type>application/octet-stream</mime_type>
         <transcode enabled="true">
           <ext>mp3</ext>
           <mime_type>audio/mpeg</mime_type>
           <dlna>MP3</dlna>
           <http_encoding>chunked</http_encoding>
           <decoder>musepack</decoder>
           <encoder>lame</encoder>
           <bitrate>192</bitrate>
           <samplerate>44100</samplerate>
         </transcode>
       </file>
       <file ext="wav">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/x-wav</mime_type>
       </file>
       <file ext="flac">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/x-flac</mime_type>
         <transcode enabled="true">
           <ext>mp3</ext>
           <mime_type>audio/mpeg</mime_type>
           <dlna>MP3</dlna>
           <http_encoding>chunked</http_encoding>
           <decoder>flac</decoder>
           <encoder>lame</encoder>
           <bitrate>192</bitrate>
           <samplerate>44100</samplerate>
         </transcode>
       </file>
       <file ext="wma">
         <type>AUDIO_ITEM</type>
         <mime_type>audio/x-ms-wma</mime_type>
         <dlna>WMAFULL</dlna>
       </file>
       <file ext="jpg">
         <ext>jpeg</ext>
         <type>IMAGE_ITEM</type>
         <mime_type>image/jpeg</mime_type>
         <convert enabled="false">
           <ext>png</ext>
           <mime_type>image/png</mime_type>
           <height>0</height>
           <width>0</width>
           <greater>false</greater>
           <less>false</less>
         </convert>
       </file>
       <file ext="bmp">
         <type>IMAGE_ITEM</type>
         <mime_type>image/bmp</mime_type>
       </file>
       <file ext="png">
         <type>IMAGE_ITEM</type>
         <mime_type>image/png</mime_type>
       </file>
       <file ext="gif">
         <type>IMAGE_ITEM</type>
         <mime_type>image/gif</mime_type>
       </file>
       <file ext="mpg">
         <ext>mpeg</ext>
         <type>VIDEO_ITEM</type>
         <mime_type>video/mpeg</mime_type>
       </file>
       <file ext="mp4">
         <type>VIDEO_ITEM</type>
         <mime_type>video/mp4</mime_type>
       </file>
       <file ext="avi">
         <type>VIDEO_ITEM</type>
         <mime_type>video/avi</mime_type>
       </file>
       <file ext="wmv">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-ms-wmv</mime_type>
       </file>
       <file ext="vob">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-ms-vob</mime_type>
       </file>
       <file ext="vdr">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-extension-vdr</mime_type>
         <transcode enabled="true">
           <ext>vob</ext>
           <mime_type>video/x-ms-vob</mime_type>
         </transcode>
       </file>
       <file ext="flv">
         <type>VIDEO_ITEM</type>
         <mime_type>application/x-flash-video</mime_type>
       </file>
       <file ext="asf">
         <type>VIDEO_ITEM</type>
         <mime_type>video/x-ms-asf</mime_type>
       </file>
       <file ext="pls">
         <type>PLAYLIST</type>
         <mime_type>audio/x-scpls</mime_type>
       </file>
       <file ext="m3u">
         <type>PLAYLIST</type>
         <mime_type>audio/x-mpegurl</mime_type>
       </file>
     </file_settings>
   </device>
   <device name="PS3" enabled="false">
     <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
     <user_agent>PLAYSTATION3</user_agent>
     <enable_dlna>true</enable_dlna>
     <transcoding_release_delay>50</transcoding_release_delay>
     <file_settings>
       <file ext="ogg">
         <type>AUDIO_ITEM_MUSIC_TRACK</type>
         <transcode enabled="true">
           <http_encoding>stream</http_encoding>
         </transcode>
       </file>
     </file_settings>
   </device>
   <device name="Xbox 360" virtual="Xbox 360" enabled="true">
       <user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
       <user_agent>Xenon</user_agent>
       <xbox360>true</xbox360>
       <file_settings>
           <file ext="mp3"><type>AUDIO_ITEM_MUSIC_TRACK</type></file>
           <file ext="jpg"><type>IMAGE_ITEM_PHOTO</type></file>
           <file ext="avi"><type>VIDEO_ITEM</type><mime_type>video/avi</mime_type></file>
       </file_settings>
       <description_values>
           <friendly_name>Our Media : Windows Media Connect</friendly_name>
           <model_name>Windows Media Connect compatible (%s)</model_name>
           <model_number>2.0</model_number>
       </description_values>
   </device>
   <device name="Telegent TG 100" virtual="default" enabled="false">
     <user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
     <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
     <playlist_style>file</playlist_style>
     <max_file_name_length>101</max_file_name_length>
   </device>
 </device_settings>
</fuppes_config>
```

vfolder.cfg
```
<?xml version="1.0" encoding="UTF-8"?>
<fuppes_vfolder_config version="0.2">

 <vfolder_layout device="default" enabled="false">

    <vfolder name="Genre">
      <vfolders property="genre">
        <items type="audioItem" />
      </vfolders>
    </vfolder>

    <vfolder name="Genre/Artists">
      <vfolders property="genre">
        <vfolders property="artist">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder>

    <vfolder name="Artists/Albums">
      <vfolders property="artist">
        <vfolders property="album">
          <items type="audioItem" />
        </vfolders>
      </vfolders>
    </vfolder> 
    
    <vfolder name="ABC/Artists/Albums">
      <vfolders split="ABC">
        <vfolders property="artist">
          <vfolders property="album">
            <items type="audioItem" />
          </vfolders>
        </vfolders>
      </vfolders>
    </vfolder>
       
    <vfolder name="Photos">
      <vfolder name="All">
        <items type="imageItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(imageItem)" />
      </vfolder>      
    </vfolder>

    <vfolder name="Videos">
      <vfolder name="All">
        <items type="videoItem" />
      </vfolder>
      <vfolder name="Folders">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>

    <vfolder name="shared dirs">
      <shared_dirs full_extend="true" />
    </vfolder>
  </vfolder_layout>

  <vfolder_layout device="Xbox 360" enabled="true">
    <vfolder name="Video" id="2">
      <vfolder name="Folders" id="21">
        <folders filter="contains(videoItem)" />
      </vfolder>
    </vfolder>
  </vfolder_layout>
</fuppes_vfolder_config>
```

fuppes_xbox.sql
```
 DELETE FROM objects WHERE device='Xbox 360';

 INSERT INTO objects (object_id,
                      detail_id,
                      type,
                      device,
                      path,
                      file_name,
                      title,
                      hidden)
      SELECT 4293918720 | object_id,
             detail_id,
             type,
             'Xbox 360',
             CASE WHEN type  = 1 THEN 'virtual'
                  WHEN type != 1 THEN path
             END,
             file_name,
             title,
             hidden
        FROM objects
       WHERE object_id<4293918720
         AND device IS NULL;

INSERT INTO objects (object_id,
                     type,
                     device,
                     path,
                     file_name,
                     title,
                     hidden)
     VALUES (2,
             1,
             'Xbox 360',
             'virtual',
             'Video',
             'Video',
             0);

INSERT INTO objects (object_id,
                     type,
                     device,
                     path,
                     file_name,
                     title,
                     hidden)
     VALUES (21,
             1,
             'Xbox 360',
             'virtual',
             'Folders',
             'Folders',
             0);

DELETE FROM map_objects WHERE device='Xbox 360';

INSERT INTO map_objects (object_id,
                         parent_id,
                         device)
     SELECT 4293918720 | object_id,
            CASE WHEN parent_id  = 0 THEN 21
                 WHEN parent_id != 0 THEN 4293918720 | parent_id
            END,
            'Xbox 360'
       FROM map_objects
      WHERE object_id<4293918720
        AND object_id NOT IN (0,21)
        AND device IS NULL;

INSERT INTO map_objects (object_id,
                         parent_id,
                         device)
     VALUES (2,
             0,
             'Xbox 360');

INSERT INTO map_objects (object_id,
                         parent_id,
                         device)
     VALUES (21,
             2,
             'Xbox 360');
```

---

### Post by BrokenKingpin on 2011-09-06
I used fuppes a while back... it is a nightmare to get working properly. I had it working on one version, but not on the latest. Eventually I just gave up on it.

I would recommend trying PS3 Media Server... despite the name, I think it works well with the 360. With this you shouldn't have to built it from source and the out of the box config actually works.

---

