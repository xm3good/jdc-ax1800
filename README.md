//拉取代码到本地编译

sudo apt-get -y install python3.7+ python3-distutils gcc-8+ g++-8+   //所需依赖

sudo rm /var/lib/dpkg/lock-frontend && sudo rm /var/lib/dpkg/lock    //可能要解锁

git clone -b ipq60xx-devel https://github.com/china-temps/openwrt.git    //直接拉取分支

或 git clone -b ipq60xx-devel_nss https://github.com/china-temps/openwrt.git    // +NSS的分支

./scripts/feeds update -a && ./scripts/feeds install -a    //更新并安装

make menuconfig     //第一项选 Qualcomm Atheros 802.11ax Wisos-s 型号就出来了

make -j8 download V=s     //下载dl库（国内请尽量全局科学上网）

make -j1 V=s        //（-j1 后面是线程数。第一次编译推荐用单线程）即可开始编译你要的固件了。
