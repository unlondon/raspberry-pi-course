raspberry-pi-course
===================

My first raspberry pi course for UnLondon

**looping gif**

![image of the board](https://raw.githubusercontent.com/james2doyle/raspberry-pi-course/master/loop.gif)

**Image**

![image of the board](https://raw.githubusercontent.com/james2doyle/raspberry-pi-course/master/board.jpg)

## Getting Started

#### Install Rasbian

* download [NOOBs offline](http://www.raspberrypi.org/downloads/) and unzip it onto the SD Card you want to use
* Choose the Rasbian option by hitting the `spacebar` and then press `i` to start the installation
* make sure your keyboard is US and not GB
* the default username and password is  "pi" and "raspberry", respectively
* once installed the system will reboot
* login with the default credentials
* you are now logged into the shell. Use `startx` to launch the desktop

#### Setup WiFi

* Run `sudo nano /etc/network/interfaces` to open the network config
* Ignore the stuff about the `eth0` device. Change the stuff about `wlan0` to the following, delete things if necessary.

```
auto lo

iface lo inet loopback
iface eth0 inet dhcp

allow-hotplug wlan0
auto wlan0

iface wlan0 inet dhcp
        wpa-ssid "networkname"
        wpa-psk "password"
```

* save the file with `ctrl+o`, confirm the filename with `y`, and press `ctrl+x` to close nano.
* restart the pi with `sudo shutdown -r now`

#### Update

* you can update the repositries with `sudo apt-get update`, accept with `y`
* Upgrade the pi with `sudo apt-get upgrade`, accept with `y`

#### Installing the required tools

* Install `git`
  * run `sudo apt-get install git`
  * accept the dependencies with `y`
  * check that git is installed with `which git`, a path should be returned

* Install node.js
  * Move to your home directory with `cd ~`
  * Run `sudo wget http://node-arm.herokuapp.com/node_latest_armhf.deb`
  * Then, `sudo dpkg -i node_latest_armhf.deb`
  * You can check everything with `which node` or `node -v`

* Install `quick2wire`
  * Clone the project with `git clone git://github.com/quick2wire/quick2wire-gpio-admin.git`
  * Then `cd quick2wire-gpio-admin`
  * Build with `make`
  * Install to the system with `sudo make install`
  * Add yourself to the userlist with `sudo adduser $USER gpio`

#### Setup the breakout board

* Plug the breakout board onto the breadboard
* Align the breakout board to the top left corner of `1-B`
* Plug the cable into the breakout board, it is keyed so no worries
* Plug the cable into the Pi, the red strip should be in the first pin (upper left)
* Connect J-3 to the bottom of the first `-`(minus) row
* Connect J-6 to I-16 with the 180Ω resistor
* Connect J-8 to H-17 with the 180Ω resistor
* Connect the Blue diode's long wire to J-17 and the short wire to the bottom of the adjacent minus row
* Connect the Red diode's long wire to J-16 and the short wire to the bottom of the adjacent minus row

![image of the board](https://raw.githubusercontent.com/james2doyle/raspberry-pi-course/master/board2.jpg)
![image of the board](https://raw.githubusercontent.com/james2doyle/raspberry-pi-course/master/board3.jpg)

#### Getting this project

* clone with `git clone https://github.com/james2doyle/raspberry-pi-course`, this will be cloned into a new folder named `raspberry-pi-course`
* change to that directory with `cd raspberry-pi-course`
* install the dependencies with `npm install`
* run the first program with `node test.js`

