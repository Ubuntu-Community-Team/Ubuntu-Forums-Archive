---
title: "Installing 32 bits Widevine deb package for Chromium (on SLAX Linux)"
date: 2024-08-17
forum: Any Other OS
---

### Post by sebastianbenito on 2024-08-17
> [FONT=arial][SIZE=3][SIZE=2]**Reply to my post (from [COLOR=#ff0000]*jmarket*[/COLOR] of PCHelpForum)**[/SIZE]
[/SIZE][/FONT]
You can use this Github repo to get it. This is the easiest way. Essentially, #1 is to install Chrome and then grab it's Widevine .so and it will auto update.

$wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -
echo 'deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main' | sudo tee /etc/apt/sources.list.d/google-chrome.list
$sudo apt update && sudo apt install -y google-chrome-stable
$git clone [https://github.com/proprietary/chromium-widevine.git](https://github.com/proprietary/chromium-widevine.git) && cd chromium-widevine && ./use-from-google-chrome.sh

and then to test it you use:

killall -q -SIGTERM chromium-browser || killall -q -SIGTERM chromium && exec $(command -v chromium-browser || command -v chromium) ./test-widevine.html &

[SIZE=2][FONT=arial]**My reply to what I quoted above:**[/FONT][/SIZE]

I have done than this partially a few weeks ago. I downloaded the latest 32 bits Chrome version and I obtained two files from it, **libwidevinecdm.so** and **libwidevinecdmadapter.so**; then I placed these two files in the **/usr/lib/Chromium** directory, and I restarted Chromium from command line at terminal and tested by opening the file *test-widevine.html*. The result of the test was as follows:

. [&#10007;] Widevine not found
. [&#10007;] audio codec audio/mp4;codecs="mp4a.40.2" not supported
. [&#10007;] video codec video/mp2t;codecs="avc1.42E01E,mp4a.40.2" not supported
. [&#10007;] video codec video/webm;codecs="vorbis,vp8" not supported
. [&#10007;] video codec video/mp4;codecs="ec-3" not supported
. [&#10007;] video codec video/mp4;codecs="avc1.42c00d" not supported

It is obvious that Widevine was not installed. What is missing in this procedure that I followed? How do I get Widevine installed and active?

---

