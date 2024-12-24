
# Hemi Network Cli-Miner Kurulumu

> herhangi bir donanıma ihtiyaç yok sunucunuza kurabilirsiniz (çoklu sunucu reposu yakında)

> (Opsiyonel) [Buradan](https://points.absinthe.network/hemi/d/connections) node kurmak istemeynler işlem yapabilir: `e2733fa6`

> (Opsiyonel) [Buradan](https://pop-miner.hemi.xyz/) da ana PC'de kurulum için.


## Kurulum Aşaması

```bash
# Öncelikle ihtiyacımız olan binary dosyasını çekiyoruz.
wget https://github.com/hemilabs/heminetwork/releases/download/v0.4.3/heminetwork_v0.4.3_linux_amd64.tar.gz

# İndirdiğimiz sıkıştırılmış dosyayı dışarı çıkaralım ve dosya içerisine girelim.
tar xvf heminetwork_v0.4.3_linux_amd64.tar.gz && cd heminetwork_v0.4.3_linux_amd64

# Miner için bir cüzdan oluşturalım.
./keygen -secp256k1 -json -net="testnet" > ~/popm-address.json

# Oluşturduğumuz cüzdan bilgilerini kontrol edelim. Mümkünse kendi bilgisayarınıza kaydedebilirsiniz.

cat $HOME/popm-address.json
```

Yukarıda sizlere ethereum_address, network, private_key, public_key ve pubkey_hash gelecek. 

Öncelikle buradan pubkey_hash olan değer ile Hemi Network discord sunucusunda faucet kanalına gidelim ve /tbtc-faucet komutunu kullanarak ardından pubkey_hash'ini address kısmına ekleyerek faucet talep edelim.

Her şey tamamlandıktan sonra aşağıdan devam edelim;

```bash
# Yeniden ubuntu sunucumuza döndük. Şimdi exportlar ile belirtelim. Ben export değerlerini kalıcı ayarlayacağım. Fakat öncelikle bir screen açalım;

screen -S hemi

# Şimdi cüzdan bilgilerimizden bize private_key kısmı gerekli. Aşağıda değiştirip uygulayın.

echo 'export POPM_BTC_PRIVKEY=PRIVATE KEY BURAYA YAZILACAK' >> ~/.bashrc
echo 'export POPM_STATIC_FEE=50' >> ~/.bashrc
echo 'export POPM_BFG_URL=wss://testnet.rpc.hemi.network/v1/ws/public' >> ~/.bashrc
source ~/.bashrc

# Daha sonra da aşağıdaki komut ile başlatabilirsiniz.
./popmd


```

Her şey bu kadardı. Biraz bekledikten sonra çıktıklarınız aşağıdaki gibi görünecek;

```json

2024-09-18 13:43:36 INFO popm popm.go:358 Mining an L2 keystone at height 1546325...
2024-09-18 13:43:38 INFO popm popm.go:426 Broadcasting PoP transaction to Bitcoin testnet3...
2024-09-18 13:43:40 INFO popm popm.go:438 Successfully broadcast PoP transaction to Bitcoin testnet3 with TX hash f2ca40b9cac97b264836541d60d392cad3c3711f8dad07d6cc042fe3ba6676b6
2024-09-18 13:43:40 INFO popm popm.go:358 Mining an L2 keystone at height 1546300...
2024-09-18 13:43:46 INFO popm popm.go:426 Broadcasting PoP transaction to Bitcoin testnet3...
2024-09-18 13:43:47 INFO popm popm.go:438 Successfully broadcast PoP transaction to Bitcoin testnet3 with TX hash c35d6a72d9e867631ea0cc76dca4281cb2e5695ed2f7a0f732362319a34d500b
2024-09-18 13:43:47 INFO popm popm.go:358 Mining an L2 keystone at height 1546275...
2024-09-18 13:43:49 INFO popm popm.go:426 Broadcasting PoP transaction to Bitcoin testnet3...
2024-09-18 13:43:50 INFO popm popm.go:438 Successfully broadcast PoP transaction to Bitcoin testnet3 with TX hash 7e0bffe54c78e8fa0e97a59be8174334dcf83674b7fb25ba4ee4f25b829cae87
2024-09-18 13:44:04 INFO popm popm.go:358 Mining an L2 keystone at height 1546350...
2024-09-18 13:44:12 INFO popm popm.go:426 Broadcasting PoP transaction to Bitcoin testnet3...
2024-09-18 13:44:14 INFO popm popm.go:438 Successfully broadcast PoP transaction to Bitcoin testnet3 with TX hash 0fa8e483f4f7cffcd358bc1c673055b7a97513349dd8a8b344278a2fb7bccc9a
```
