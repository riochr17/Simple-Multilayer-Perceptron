# Simple Multilayer Perceptron

A Python implementation of multilayer perceptron neural network

Note: formulasi perhitungan multilayer perceptron dapat dilihat [disini](mlp-formula)

## Installation

Make sure that you have numpy library installed

## Usage

```python
instance = MLP(layers, learning_rate = 0.5, momentum = 0, mini_batch = 1, print_batch_progress = False, full_testing_periode = 1, print_testing_detail = False, print_error_progress = False)
```

Example using pre-trained model
```python
from mlpmat import MLP

# init MLP instance
mlp = MLP([2, 5, 3, 1], learning_rate = 0.15)

# load saved model
mlp.loadModel("model/xor2531")

# predict using model
print mlp.predict([1, 1])
print mlp.predict([1, 0])
print mlp.predict([0, 1])
print mlp.predict([0, 0])

```

Example train and save model
```python
from mlpmat import MLP

# init MLP instance
mlp = MLP([2, 5, 3, 1], learning_rate = 0.15)

# feed training data
mlp.TrainData.append([[1, 1], [0]])
mlp.TrainData.append([[1, 0], [1]])
mlp.TrainData.append([[0, 1], [1]])
mlp.TrainData.append([[0, 0], [0]])

# training using 10000 epoch
mlp.train(10000)

# test trained mlp
print mlp.predict([1, 1])
print mlp.predict([1, 0])
print mlp.predict([0, 1])
print mlp.predict([0, 0])

# save model
mlp.saveModel("model/xor2531")

```

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## Current Issue

- Parameter konstruktor masih ambigu.
- MLP tidak melakukan normalisasi pada data masukan, sehingga data input (latih atau uji) yang diberikan harus di normalisasi terlebih dahulu (jika dibutuhkan).
- Backpropagation menggunakan basic SGD (Stochastic Gradient Descent) dengan variasi momentum saja.
- Kumulasi error dihitung dengan melakukan full testing setelah satu epoch selesai, dapat dioptimasi dengan menghitung error saat backpropagation.
- Model yang disimpan hanya berupa weight dan bias saja tidak menyimpan konfigurasi layer mlp, sehingga ketika memuat model harus inisialisasi layer terlebih dahulu.

## Credits

TODO: Write credits

## License

TODO: Write license