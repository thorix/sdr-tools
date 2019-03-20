# Decoding pager transmissions with a rtl-sdr
This will get you setup to decode POCSAG/Flex. For more info go here:
https://www.rtl-sdr.com/rtl-sdr-tutorial-pocsag-pager-decoding/

Will try these later
```
https://github.com/pagermon/pagermon
https://www.raspberrypi.org/forums/viewtopic.php?t=45142
```

### Install rtl_fm
```
brew install rtl-sdr
```

### Install multimon-ng
http://www.fwd4.com/post/149226197049/compiling-multimon-ng-on-macos-and-parsing-pager
```
git clone https://github.com/EliasOenal/multimon-ng.git
cd multimon-ng
mkdir build
brew install qt
cd build
qmake ../multimon-ng.pro PREFIX=/usr/local
```
I had to do the following on my system
```
cd build
make
sudo cp multimon-ng /usr/local/bin/
```

### The command
```
sudo rtl_fm -f 929.634M -M fm -s 22050  | multimon-ng -t raw -a POCSAG512 -a POCSAG1200 -a POCSAG2400 -a FLEX -
```

#### radio bands that worked for me:
929.620M
929.617M
