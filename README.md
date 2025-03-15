public class Persona {
    String nombre, apellido;
    int edad;
    public Persona(String nombre, String apellido, int edad) {
        this.nombre = nombre;
        this.apellido = apellido;
        this.edad = edad;
    }
    @Override
    public String toString() {
        return "Persona{" + "nombre=" + nombre + ", apellido=" + apellido + ", edad=" + edad + '}';
    }  
}
public class CycleSort {
    public static void cycleSort(Persona[]arreglo){
        int tamaño = arreglo.length;   
        for (int i = 0; i < tamaño-1; i++) {
            Persona item = arreglo[i];
            int posicion = i;      
            for (int j = i+1; j < tamaño; j++) {
                if(arreglo[j].apellido.compareTo(item.apellido) < 0){
                    posicion++;
                }
            }
            if(posicion == i){
                continue;
            }
            while(item.apellido.equals(arreglo[posicion].apellido)){
                posicion++;
            }            
            Persona temporal = arreglo[posicion];
            arreglo[posicion] = item;
            item = temporal;            
            while (posicion != i){
                posicion = i;
                for (int j = i + 1; j < tamaño; j++) {
                    if(arreglo[j].apellido.compareTo(item.apellido) < 0){
                        posicion++;
                    }
                }               
                while(item.apellido.equals(arreglo[posicion].apellido)){
                    posicion++;
                }          
                temporal = arreglo[posicion];
                arreglo[posicion] = item;
                item = temporal;
            }
        } 
    }
}
public static void main(String[] args) {
        System.out.println(" hola ");
        Persona[] personas = {
            new Persona("Carlos", "Gomez", 30),
            new Persona("Ana", "Martinez", 25),
            new Persona("Luis", "Fernandez", 40),
            new Persona("Pedro", "Alonso", 35),
            new Persona("Maria", "Hernandez", 28)
        };
        System.out.println("Lista antes de ordenar:");
        for (Persona p : personas) {
            System.out.println(p);
        }
        CycleSort.cycleSort(personas);
        System.out.println("\nLista despues de ordenar:");
        for (Persona p : personas) {
            System.out.println(p);
        }
    }
