# live-earth-desktop

There's a satellite called Himawari-8 which is geostationary over approximately Papua New Guinea. The very excellent people who run this satellite have set up a [live stream](http://himawari8.nict.go.jp/) of the ultra-high-res images that it takes. They are gorgeous.

Similarly, there's another satellite called GOES-East. It's above South America at the equator, and its photos are just as amazing as the Himawari ones. Because the NOAA is excellent people too, they also have [live images available](https://www.star.nesdis.noaa.gov/GOES/GOES16_FullDisk.php).

Inspired by [someone awesome on Reddit](https://www.reddit.com/r/programming/comments/441do9/i_made_a_windows_powershell_script_that_puts_a/), and based on a script by [celoyd](https://github.com/celoyd), I built a script that downloads the latest photo. With a `plist` file for `launchd` on OS X, I can run this script every ten minutes and always have the latest image on my machine. And then by setting my OS X desktop to a slideshow of the images inside a folder, the latest Himawari-8 or GOES-East photo is always set as my desktop image.

![](example.png)

## Instructions

1. Clone this repo
1. Pick whether you want images of Australia and Southeast Asia (Himawari) or the Americas (GOES-East).
2. Change the paths set in `tmp` and `out` and `os.system("rm ...")` in `himawari.py` or `goes-east.py` to paths inside this directory.
3. `ln -s <this-dir>/himawari.plist /Users/<you>/Library/LaunchAgents/` or `ln -s <this-dir>/goes-east.plist /Users/<you>/Library/LaunchAgents/`
4. `launchctl /Users/<you>/Library/LaunchAgents/himawari.plist` or `launchctl /Users/<you>/Library/LaunchAgents/goes-east.plist` to start it running every 10 minutes
5. Go to OS X Preferences > Desktop and Screen Saver and set your desktop to rotate through the images contained in the `images` directory that you're writing these images to (whatever directory you made `out` point to).
6. Enjoy!
